---
title: "rubyripper problems - lucid ruby 1.8 / 1.9 / libgtk2-ruby"
date: 2010-04-26
forum: Multimedia Software
---

### Post by rents1977 on 2010-04-26
I've been using rubyripper quite happily on Karmic, now I've moved to Lucid and discovered a bit of an issue.

rubyripper will pause for several minutes between tracks with ruby 1.8. If I upgrade to ruby 1.9.1 the gui client won't run due to an issue with libgtk2-ruby not being available for 1.9.1.

The cli version of rubyripper under 1.9.1 is blazingly fast, so that is what I'm using at the moment, but I do prefer the gui.

Anyone have any insight into this? Googling suggests there may be a bug in ruby 1.8.7 that caused the long pauses, but it was supposed to have been fixed in 1.8.7.249 i.e. the default Lucid version.

---

### Post by mikechant on 2010-05-02
Just upgraded to 10.04 and I'm getting exactly the same problem.

No solution yet.

---

### Post by fatboab on 2010-05-06
I tried installing rubyripper from the ppa and while it appeared to work, I  couldn't find the app to run it, I'm on Kubuntu if that makes any  difference. I had ruby 1.8 installed and ran into the same problem you did. So I installed ruby1.9.1, and running the cli script it  doesn't rip anything, it just creates the folder, .cue  and .m3u files  and then exits. This is the log:

```
This log is created by Rubyripper, version 0.5.7
Website: http://code.google.com/p/rubyripper

Cdrom player used to rip:
HL-DT-ST DVDRAM GSA-4083N 1.08
Cdrom offset used: 0

Ripper used: cdparanoia --never-skip=40
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-flac     -> -5 -V (flac 1.2.1)

CDDB INFO

Artist    = Balance
Album    = 016 - Agoria (Disk 1)
Year    = 2010
Genre    = Tech House, Minimal
Tracks    = 25

01 - Gregg Kowalsky - Ashes From Evermore
02 - Alva Noto - Xerrox Monophaser 2 / DJ Koze - Lords Of Panama
03 - Mark Pitchard - ?
04 - Manvoy de Saint Sadrill - Soeheniona
05 - Tisca - Joe Si Ha
06 - Emiliana Torrini - Gun
07 - Agoria - Parasite 2
08 - Arandel - In D#5
09 - Messina - Columpnam
10 - 19.454.18.5.25.5.18 - When I Think Of
11 - Pom Pom - IO
12 - Agoria - Altre Voci
13 - Glimpse - Train In Austria Part 2
14 - The Field  - Over The Ice (Live Mix)
15 - Olibusta - La Pazz
16 - Cubenx - Mis Dias Y Tus Noches
17 - Felix Laband - Whistling In Tongues (Todd Terje Remix)
18 - Jozif - Back 2 My Roots (Jozif's 5 O'Clock Fabric Shadow Edit)
19 - Bibio - Jealous of roses
20 - LCD Soundsystem  - 45:33 (Trus'me Remix)
21 - Bozoo Bajou feat Rumer - Same Sun (Prins Thomas Diskomiks) / Oxia -  Less Time
22 - Hatikvah - Synchronicty (Block Barley & Engin Ozturk Holmby  Hills Remix)
23 - Rio en Medio - The Last Child's Tear
24 - Tipper - Just As The Sun Went Down
25 - Gregg Kowlasky - Ashes From Evermore / Alva Noto - Xerrox  Monophaser 2

STATUS


```

Did you do anything specific to get it running under ruby 1.9.1...?

Cheers,

---

### Post by rents1977 on 2010-05-07
Sorry fatboab, after installing 1.9.1 I tried to run the gui client and it failed, so I tried running the gui via terminal and it complained about the missing ruby-gtk2 library. I just typed rrip_cli to run the in the terminal from then on.

You can set the options if you start rrp_cli with the drive empty.

Mine is set for flac encoding options --best -V

---

### Post by mikechant on 2010-05-29
I installed ruby 1.9 and changed the /usr/bin/ruby link to point to it to make it the default, and rrip_cli works fine now. I pretty much always rip with the same parameters so this works well for me.

---

### Post by mahavishnu on 2010-08-10
I was a happy user of Rubyripper using Hardy.

Now I'm using Lucid and running Rubyripper is quite a nightmare.
I've tried version 0.5.7 and 0.6 and the same issue: "Analizing files for mismatching chunks" takes forever...

I was used to take 5 to 10 minutes to encode a single CD now it takes one hour and a half !!!!

---

### Post by mc4man on 2010-08-10
> I was a happy user of Rubyripper using Hardy....

Set up rr in the gui, but rip from the terminal
For interactive
```
rrip_cli
```
To just auto rip (0.6
```
rrip_cli -d
```
To fix the gui on lucid and or maverick requires switching default 'ruby' to the 1.9.X version and supplying a new ruby-gtk2 built off of ruby 1.9.X
( did here but the gui/cli method is easier

---

### Post by mahavishnu on 2010-08-15
> **mc4man said:**
> Set up rr in the gui, but rip from the terminal
To just auto rip (0.6
```
rrip_cli -d
```


you mean **rrip_cli -a**
anyway, now it takes 5 minutes to rip a CD..
thanks..

---

### Post by mc4man on 2010-08-15
> you mean rrip_cli -a

No, not really - depends on version of rr
For 0.6 or higher - rrip_cli -d
For less than 0.6 - rrip_cli -a

---

