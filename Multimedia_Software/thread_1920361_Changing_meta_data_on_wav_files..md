---
title: "Changing meta data on wav files."
date: 2012-02-04
forum: Multimedia Software
---

### Post by Damascushead on 2012-02-04
I have some music that I have recorded that are in 16 bit 44.1khz format and I need to add track ordering, artist info, album title. etc. I downloaded EasyTag however it does not support (or even recognize any wav files.) 

I know some might say I should just convert to ogg, but in order to collaborate with others I need to remain in wav format. (Unfortunately ProTools on my windows machine does not allow this information to be set upon exporting.)

 Is there some sort of software in the repository that will let me do this, so that when viewed on other systems it will read the titles, artist, etc? I really hope so. 

Any suggestions would be great.:)

Peace and Music

---

### Post by ron999 on 2012-02-04
> **Damascushead said:**
> 
Any suggestions would be great.:)


Hi
I don't think that wav files support metadata.:(
That's probably why EasyTag doesn't recognize them.;)

---

### Post by mc4man on 2012-02-05
> **ron999 said:**
> Hi
I don't think that wav files support metadata.:(
That's probably why EasyTag doesn't recognize them.;)
You can though not sure of a linux native solution  (& it can be a bit sketchy

Every once & a while I use dBpoweramp running in wine because it's quite a remarkable piece of software (one easy way to produce almost any test audio file

Anyway it will tag .wav - see screen, though I've never looked at if/how it could edit those tags though probably it can

to see (21 day trial that lasts *quite *a bit longer in wine
[http://www.dbpoweramp.com/cd-ripper.htm](http://www.dbpoweramp.com/cd-ripper.htm) *also converts file to file
[http://www.dbpoweramp.com/codec-central.htm](http://www.dbpoweramp.com/codec-central.htm)
[http://www.dbpoweramp.com/dbpoweramp-dsp.htm](http://www.dbpoweramp.com/dbpoweramp-dsp.htm)

---

### Post by Damascushead on 2012-02-05
Thanks for the suggestions. I think I might try dBPoweramp. What I am really trying to do is avoid using Nero or Toast or some other overly priced software, which I know will do the job. 

Thank you. I will give her a shot.

:)

---

### Post by shantiq on 2012-02-05
> **mc4man said:**
> 

Anyway it will tag .wav - see screen, though I've never looked at if/how it could edit those tags though probably it can




did u achieve this through Wine mc?

the cdripper does not seem to see the files in the drive on my system
i have created a drive called R: in winecfg  and pointed it at cdrom
but still no cigar

PS   dbpoweramp is a mighty thing of beauty  the converters are awesome

---

### Post by mc4man on 2012-02-05
> **shantiq said:**
> did u achieve this through Wine mc?

the cdripper does not seem to see the files in the drive on my system
i have created a drive called R: in winecfg  and pointed it at cdrom
but still no cigar

PS   dbpoweramp is a mighty thing of beauty  the converters are awesome

That was from a conversion 

As far as audio cd's, saw same thing

Took a bit of doing but got it going, can post up tonight how to do so, (maybe 11 pm or so - 4-5 am for you

Basically had to add a static mount point in /media, add the drive to fstab, configure wine to see that mountpoint as a cd drive, then all good

(fstab deal here
[http://ubuntuforums.org/showthread.php?t=1744494](http://ubuntuforums.org/showthread.php?t=1744494)

---

### Post by shantiq on 2012-02-05
thanx yes will appreciate that

this is what i get from > sudo lshw -C disk

> *-cdrom
       description: DVD writer
       product: DVD_RW ND-3550A
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.52
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready


---

### Post by mc4man on 2012-02-05
> **shantiq said:**
> thanx yes will appreciate that

this is what i get from

open a terminal

```
sudo mkdir -p /media/cdrom0
```

```
sudo gedit /etc/fstab
```

Add a new line at the bottom, save & close
```
/dev/sr0   /media/cdrom0   udf,iso9660  user,noauto,exec   0 0
```

Then do a full restart

Open winecfg, click on drives
Click on "add", the pop up will likely show D, click Ok
While D is still highlighted in the drive box,  fill in path in the "Path" box

/media/cdrom0/

Again select D & click on "Show Advanced", in the "Type" dropdown select "CD-ROM"
Finally click on Apply, close winecfg

Insert an audio cd, open dB & see - if you wish, open winecfg - it should show similar to screen above

If a go the best choice here for lookup in trial version is 'freedb', click on the meta icon, in the dropdown

---

### Post by shantiq on 2012-02-06
thanx for this

all goes swimmingly up to >  Again select D & click on "Show Advanced", in the "Type" dropdown select "CD-ROM"

when it does** not **show info in the last two boxes [label and serial] they are greyed out


[CENTER][ATTACH]212134[/ATTACH][/CENTER]

and therefore does not see tracks in DB

Might be my version of Wine   1.3.28

---

### Post by Damascushead on 2012-02-06
THX :)
 
I previously uninstalled wine for security purposes, but am willing to reinstall to get this done. 
 
And now shantiq I will know how to get wine to recognize my drive.
 
Take it easy

---

### Post by mc4man on 2012-02-06
> **shantiq said:**
> thanx for this

all goes swimmingly up to 

when it does not show info in the last two boxes [label and serial] they are greyed out


[CENTER][ATTACH]212134[/ATTACH][/CENTER]

and therefore does not see tracks in DB

Might be my version of Wine   1.3.28

That shouldn't matter, I probably should of used a different screen. That info would only show if you set up the drive *While an audio cd was in the drive.* From then on it would show as you've posted if no audio cd was in the drive.

If still having issues - 1st put an audio cd in the drive, then open winecfg, Highlight the D drive by clicking on the "D"
Remove it, then set it up again as before.

---

### Post by shantiq on 2012-02-06
again thank you but something still not clicking here
with the disc in the drive i still get this
it does not see the tracks/disc

[ATTACH]212148[/ATTACH]

---

### Post by mc4man on 2012-02-06
shantiq - 
Not sure why your difficulty - was on 12.04 but switched to 11.10 & tried again

Without doing anything dB couldn't find a drive - screen 1

Set up the /media/cdrom0 & fstab, **restarted** then added the drive in winecfg
Didn't actually matter if I left the D on auto-detect or specified CD-ROM in advanced, after setting clicked apply, closed winecfg, inserted an audio cd.
Then when re-opening winecfg, highlighting D & clicking on Advaced shows as in screen 2, it found the audio cd

At that point dB works fine - screen 3

( the manual meta is quite cool - though iirc after the 21 day only freedb works? screen 4
Hope you get it going - if dB used WNASPI32.DLL then this wouldn't be an issue, the prog. would access the drive directly without winecfg ala EAC, ImgBurn ect.

---

### Post by shantiq on 2012-02-06
thank you for your help
as usual with me a basic mistake:KS
for reasons best known to the spazz aspect of my illogical mind

i had entered

```
#  /dev/sr0   /media/cdrom0   udf,iso9660  user,noauto,exec   0 0
```

instead of

```
/dev/sr0   /media/cdrom0   udf,iso9660  user,noauto,exec   0 0
```


and of course nothing else could work


thank you for your patience.  No doubt it will help others too
[B]
PS[/B]   electric ladyland   hhooohaaa   does not/has not/will not get better  :KS:KS

---

### Post by mc4man on 2012-02-06
shantiq - glad your back in business

(saatchionline is an interesting place

---

### Post by Damascushead on 2012-02-07
Amen to Electric Ladyland.

---

### Post by mc4man on 2012-02-07
A little fool around with dB

Adding either the cd ripper or converter to unity panel
(can be done as 1 icon - adding one or the other as a quicklist but for the moment as separate

To add the converter - assumes ~/.local/share/applications exists - to check/create if not there
```
mkdir -p ~/.local/share/applications
```

```
gedit ~/.local/share/applications/musicconverter.desktop
```

C&P this in, save, the "Name=" can be whatever you wish, if different icon then full path
The Path= line is maybe not needed,if leaving change red to your username
```
[Desktop Entry]
Name=dBpowerAmp Music Converter
Exec=wine "C:\Program Files\Illustrate\dBpoweramp\MusicConverter.exe" 
Type=Application
StartupNotify=true
Path=/home/[COLOR="Red"]doug[/COLOR]/.wine/dosdevices/c:/Program Files/Illustrate/dBpoweramp
Icon=8939_MusicConverter.0
```

Then open the folder & drag the .desktop on to unity launcher
```
nautilus ~/.local/share/applications
```

(I've tried adding a mimetype= line for DnD of files - doesn't quite work, may be able to figure out may not


To add the cd ripper```

gedit ~/.local/share/applications/dbpoweramp.desktop
```

add this - 
```
[Desktop Entry]
Name=dBpowerAmp Cd Ripper
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\Illustrate\\\\dBpoweramp\\\\CDGrab.exe %U
Type=Application
StartupNotify=true
Path=/home/[COLOR="Red"]doug[/COLOR]/.wine/dosdevices/c:/Program Files/Illustrate/dBpoweramp
Icon=B941_CDGrab.0
MimeType=x-content/audio-cdda;

```
Same deal as above, drag on to launcher

To use the ripper as auto run on cd insertion on 11.10/12.04
**Do a log out/in after above**
Open System Setting > Removable media > Cd audio > other application, you should see it there, select - screen

If not there
```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section add or edit to this line
```
x-content/audio-cdda=dbpoweramp.desktop
```

You should also add to same line in the [Added Associations] section
if line is there the append to end -
Ex
> x-content/audio-cdda=vlc-cd.desktop;dbpoweramp.desktop;

Or if no line then just add
```
x-content/audio-cdda=dbpoweramp.desktop;
```

---

### Post by shantiq on 2012-02-08
ok one more question since i trip up at every step:KS

and the answer here might simply be because you have gone over 21 days ; but it might not be so i shall ask


i do not get connection to tagging here [ATTACH]212274[/ATTACH]refreshing changes nowt


and if i go to configuration it shows i have not got a connection[ATTACH]212275[/ATTACH]no address no port


how can i remedy that if at all possible?

---

