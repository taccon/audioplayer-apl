# audioplayer3 APL

This repository describes APL playlist formats for taccon audioplayer.

## Playlist formats for taccon audioplayer so far

- APL (ini based) (~2000)
- AP2 (ini based) (~2004)
- APX (xml based) (2010)
- AP3 (json) (2016)

### Audioplayer Playlist (APL)

When the first version of audioplayer that supported playlists was released approx. in 2000, APL was introduced to store them. It was a very simple INI based format.

### APL v2 (AP2)

The AP2 format was introduced in 2004 with the first audioplayer3. It was still INI based but added more options that were mainly used for supporting internal playlists.

Sample playlist file

    [APLv2-Playlist]
    EntryCount=10
    FileName1=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\1 Crystall.ogg
    Entry1=New Order - Crystall
    FileName2=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\2 60 Miles an hour.ogg
    Entry2=New Order - 60 Miles an hour
    FileName3=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\3 Turn my way.ogg
    Entry3=New Order - Turn my way
    FileName4=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\4 Vicious streak.ogg
    Entry4=New Order - Vicious streak
    FileName5=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\5 Primitive notion.ogg
    Entry5=New Order - Primitive notion
    FileName6=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\6 Slow jam.ogg
    Entry6=New Order - Slow jam
    FileName7=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\7 Rock the shack.ogg
    Entry7=New Order - Rock the shack
    FileName8=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\8 Someone like you.ogg
    Entry8=New Order - Someone like you
    FileName9=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\9 Close range.ogg
    Entry9=New Order - Close range
    FileName10=C:\Dokumente und Einstellungen\thommy\Eigene Dateien\Eigene Musik\Ogg\New Order - Get Ready\10 Run wild.ogg
    Entry10=New Order - Run wild
    StartEntry=5
    ShuffleMode=0
    PlayMode=Normal

### Chorus Web XML (APX)

In 2010 a Flash-based web version of audioplayer was introduced (named *Chorus*). It supported the XML based APX format which was planned to also be the future default playlist format for upcoming Desktop versions of the player. The idea was to allow simple export for artists from the Desktop player to the web player to make songs available to their audience.

Sample playlist file

    <apx name="Test-Mix">

        <options>
            <repeatlist />
            <shuffle />
        </options>
        
        <song>
            <repeat>2</repeat><!-- possible values: yes (1 repeat), no (no repeat), (number of repeats) -->
            <resource>./music/Fireflies.mp3</resource>
            <artist>Owl City</artist>
            <title>Fireflies</title>
            <totaltime>3'50</totaltime> <!-- possible values: 03:50 / 3:50 / 3'50 / ..., 230000 -->
        </song>

        <song>
            <title>Chinese</title>
            <resource>./music/song.mp3</resource>
        </song>
        
    </apx>

### APL v3 (AP3)

AP3 was introduced beginning of 2016 during a complete rewrite of audioplayer3. It is a JSON based format that is described in a first draft [here](schema/ap3.v1.0.schema.json) as [JSON schema](http://json-schema.org). The format is going to be extended to allow smart playlists (e.g. folder based filters or searches).

Sample playlist file

    {
      "name": "Polarkreis 18 - The Color Of Snow",
      "entries": [
        {
          "source": "/Users/thommy/Music/Polarkreis 18 - The Color Of Snow/Polarkreis 18 - 130-70.mp3"
        },
        {
          "source": "/Users/thommy/Music/Polarkreis 18 - The Color Of Snow/Polarkreis 18 - Allein Alene (Nephew Remix).mp3"
        },
        {
          "source": "/Users/thommy/Music/Polarkreis 18 - The Color Of Snow/Polarkreis 18 - Allein Allein.mp3"
        }
      ]
    }

Values for the `source` attribute can be:

- Absolute pathes
- Relative pathes regarding the playlist file location
- URLs