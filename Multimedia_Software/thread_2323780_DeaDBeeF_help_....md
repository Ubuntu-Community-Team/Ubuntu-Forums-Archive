---
title: "DeaDBeeF help ..."
date: 2016-05-08
forum: Multimedia Software
---

### Post by czgirb on 2016-05-08
saw this on [http://deadbeef.sourceforge.net/screenshots/0.6/07.png](http://deadbeef.sourceforge.net/screenshots/0.6/07.png)
how can i have this kind of **spectrum** ... which placed on artwork's right side
**Thank you**

---

### Post by Imerion on 2016-05-08
DeaDBeeF can be customized in pretty much any way you want. To do this, go to View, activate Design Mode and you can move around and change size of various elements. Right-Click to change what they display. The spectrum you are looking for should be in the Replace With-menu. Good luck!

---

### Post by shantiq on 2016-05-11
[FONT=arial]ha [**[COLOR=#000000]czgirb[/COLOR]**]("http://ubuntuforums.org/member.php?u=1614766")  it is not technically a spectrum   but called [Waveform Seekbar]("http://deadbeef.sourceforge.net/plugins.html")   allows you to see waveform and move up and down your track


&#10122;  [download ]("http://sourceforge.net/projects/deadbeef/files/plugins/x86_64/ddb_waveform_seekbar-0402f6d-x86_64.zip/download")
&#10123; Then to place them in the right place
it says to do this on the [designer's page]("https://github.com/cboxdoerfer/ddb_waveform_seekbar")

&#10124; but if you have installed the deb route you will need to  open and extract both .so files to Home folder and then move them to

[/FONT]```
 sudo mv *ddb_misc_waveform*  /opt/deadbeef/lib/deadbeef
```[FONT=arial]


** then to go to Deadbeef check it is in your plugins**

&#10125;   do what was suggested in previous post ie   click on View/Design Mode  then to right click and move boxes around   ;   the navigation to move them around is NOT instinctive

this is the best i could manage:::   you might be more astute than I :]

[/FONT]


edit :  more details

[[IMG]http://s32.postimg.org/gzlnw8z6p/image.jpg[/IMG]]("http://postimg.org/image/gzlnw8z6p/")[[IMG]http://s32.postimg.org/3soe3f1kx/image.jpg[/IMG]]("http://postimg.org/image/3soe3f1kx/")

&#10122; to get the album art on fresh install
right-click on &#9835; and pick Add Column
&#10123; on Type pick Album Art then right click on where it now says "Album Art" and pick Group by artist
now you see your artwork
&#10124; Now go >> View/Design mode and right-click on Progress Bar >> Replace With Waveform Seek
do same again with Controls and left-hand side if you want the Artwork there
&#10125; Here i set the Global Hotkey to CTRL+1 to control Pause/Play

This should explain it :]


[FONT=arial]PS   you will want this maybe while you move things around if it does not work first time

[/FONT]
```
 rm    ~/.config/deadbeef/config
```   then your gui will be reset to original

---

### Post by mc4man on 2016-05-11
> **shantiq said:**
> 

&#10124; but if you have installed the deb route you will need to  open and extract both .so files to Home folder and then move them to

sudo mv  *ddb_misc_waveform* [FONT=arial] /opt/deadbeef/lib/deadbeef

&#10125;   do what was suggested in previous post ie   click on View/Design Mode  then to right click and move boxes around   ;   the navigation to move them around is NOT instinctive


The designer mode is ill-designed at best, I find it a complete pita.
Extra plugins can also go into ~/.local/lib/deadbeef (location needs to be created

---

### Post by shantiq on 2016-05-11
:D   had   to check[ pita]("http://www.urbandictionary.com/define.php?term=pita") mc   never heard this here   only one I know is pitta  ..   the greek/arab flat bread  ;    and yes it is   the designer mode is a heck of a bread   ....    still a cool player  ;    sound is not the best  like Audacious with crystalizer or xmms   but good

**PS** sound can be slightly "ameliorated" by using Home theater preset out of [those]("http://ubuntuforums.org/showthread.php?t=1503749&p=11764546#post11764546")  View/Equalizer >> upload preset ; try the others see what works best on your setups
also this trick helps too >>   tick them all
[[img]http://s20.postimg.org/br8c5m07t/image.jpg[/img]](http://postimg.org/image/br8c5m07t/)

---

### Post by czgirb on 2016-05-16
thank you. installed as your guidance. 
that is L/R spectrum/wafeform seekbar.
but i also see only **ONE** one spectrum/waveform seekbar .., what it's called?
Thank you.



> **shantiq said:**
> [FONT=arial]ha [**[COLOR=#000000]czgirb[/COLOR]**]("http://ubuntuforums.org/member.php?u=1614766")  it is not technically a spectrum   but called [Waveform Seekbar]("http://deadbeef.sourceforge.net/plugins.html")   allows you to see waveform and move up and down your track


&#10122;  [download ]("http://sourceforge.net/projects/deadbeef/files/plugins/x86_64/ddb_waveform_seekbar-0402f6d-x86_64.zip/download")
&#10123; Then to place them in the right place
it says to do this on the [designer's page]("https://github.com/cboxdoerfer/ddb_waveform_seekbar")

&#10124; but if you have installed the deb route you will need to  open and extract both .so files to Home folder and then move them to

[/FONT]```
 sudo mv *ddb_misc_waveform*  /opt/deadbeef/lib/deadbeef
```[FONT=arial]


** then to go to Deadbeef check it is in your plugins**

&#10125;   do what was suggested in previous post ie   click on View/Design Mode  then to right click and move boxes around   ;   the navigation to move them around is NOT instinctive

this is the best i could manage:::   you might be more astute than I :]

[/FONT]


edit :  more details

[[IMG]http://s32.postimg.org/gzlnw8z6p/image.jpg[/IMG]]("http://postimg.org/image/gzlnw8z6p/")[[IMG]http://s32.postimg.org/3soe3f1kx/image.jpg[/IMG]]("http://postimg.org/image/3soe3f1kx/")

&#10122; to get the album art on fresh install
right-click on &#9835; and pick Add Column
&#10123; on Type pick Album Art then right click on where it now says "Album Art" and pick Group by artist
now you see your artwork
&#10124; Now go >> View/Design mode and right-click on Progress Bar >> Replace With Waveform Seek
do same again with Controls and left-hand side if you want the Artwork there
&#10125; Here i set the Global Hotkey to CTRL+1 to control Pause/Play

This should explain it :]


[FONT=arial]PS   you will want this maybe while you move things around if it does not work first time

[/FONT]
```
 rm    ~/.config/deadbeef/config
```   then your gui will be reset to original

---

