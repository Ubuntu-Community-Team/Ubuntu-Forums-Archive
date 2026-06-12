---
title: "[$50 Reward] Rhythmbox Crash on Ipod Mount"
date: 2009-05-02
forum: Multimedia Software
---

### Post by EggMasta on 2009-05-02
Hey guys,I have a problem here. I keep my 80 gig ipod classic updated through rhythhmbox, and have had no problems at all for 6 months. But recently, on my 8.10 install, when ever I mount my ipod, Rhythmbox opens for a few seconds, freezes, then closes. I can still play files locally off my hard drive. I can however, access the drive of my ipod and view the files manually, so I do not think the hard drive is corrupted. I tried upgrading to 9.04, and uninstalling and reinstalling rhythmbox but that didnt seem to help.

I have a massive road trip coming up, and if I cannot update my ipod before I go, I will be one unhappy camper. So if anyone helps me find a way to fix this, I will pay them $50 (or what ever equivalent in euros, pounds, etc) through PayPal.

---

### Post by GreenBowlPacker_3 on 2009-05-02
Are you still using 9.04?

---

### Post by EggMasta on 2009-05-02
Yup still 9.04 as of now. And I tried amarok, and it gives the same problem

---

### Post by GreenBowlPacker_3 on 2009-05-02
Is everything up to date?

---

### Post by graysky on 2009-05-02
Do either of those apps store configuration files in your home directory?  You might wanna look for some dot directories (i.e. ~/.rhythmbox or the like).  You can bring up a listing of all your hidden dirs like this:
```
$ ls -lha
```

Anyway, if you find something interesting, simply rename it to something else (for example .Virtualbox could be renamed (via the mv command) to .Virtualbox-old).  By removing the dot directory, you'll force the app to recreate it with fresh settings.

---

### Post by golusweet on 2009-05-02
Install Banshee

---

### Post by gnulogic on 2009-05-02
use Songbird it is an open source replacement for itunes on ubuntu.  If my solution helps make a donation to the Free Software Foundation they have made it possible for us to compute in freedom with most of the free software we use.

---

### Post by neu2buntu on 2009-05-02
[SIZE=4]goto my post #10 1st then try this on failure...[/SIZE]launch ```
rhythmbox
``` from terminal and redo everything to make it crash out. then post the output here ..also try ```
rhythmbox -d
``` or possibly ```
strace rhythmbox
``` (this spits out a lot of output) or ```
time rhythmbox
```.... also just uninstalling rhythmbox can leave some config files behind so try 
```
sudo apt-get --purge remove rhythmbox
```:guitar: then reinstall it!!!!


also if my memory serves me right,.you may find that the terminal dissapears after a crash ,if so then use & after commands  eg ```
rhythmbox &
``` ... i think this is the correct symbol to pass here!!!

---

### Post by drharence on 2009-05-02
thats great. you can do that with any app... :)

---

### Post by neu2buntu on 2009-05-02
think i might be onto something here do code ```
gconf-editor
``` and choose >apps>rhythmbox>plugins>ipod.....click on this folder icon and tick "active" and untick "hidden"

---

### Post by EggMasta on 2009-05-03
Running from terminal gives this:
```

owner@owner-laptop:~$ rhythmbox

(rhythmbox:10016): Rhythmbox-WARNING **: Could not open device /dev/radio0

** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 30000000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 7500000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 43520000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 10880000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 22160000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 5540000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 74400000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 18600000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 16320000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4080000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 18880000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4720000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 18960000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4740000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19040000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4760000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19120000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4780000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19200000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4800000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19280000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4820000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19360000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4840000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19440000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4860000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19520000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4880000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19600000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4900000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19680000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4920000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1029, offset: 19760000


** (rhythmbox:10016): WARNING **: Unexpected image type in mhni: 1028, offset: 4940000

Bus error

```

---

### Post by EggMasta on 2009-05-03
Anyone got any ideas?

---

### Post by neu2buntu on 2009-05-03
u still got this problem..lol..?  did you try purging rhythmbox and reinstalling from 1 of my earlier posts? one thing to try also if any of your friends have an ipod is try it with rhythmbox,.and obviously if there are no errors the problem is with the ipod...

---

### Post by neu2buntu on 2009-05-03
right try this ... goto synaptic package manager and in the search icon type > libgpod and post what is installed out of this list.... some of these libs dont allow for artwork (ie images) so this maybe what is locking rhythmbox up!!!!

---

### Post by mc4man on 2009-05-03
When you apt-get purge rhythmbox there are 3 main things left behind, all in home folder (hidden files

So apt-get purge rythmbox, then

.cache/rhythmbox  - your covers, *probably can leave* or rename, temporally  copy elsewhere, whatever

.gconf/apps/ - delete or rename the rhythmbox folder

.gnome2/  - delete or rename the rhythmbox folder


After deleting those 2 folders do a Ctrl+Alt+Delete to restart, reinstall rythmbox and see

---

### Post by EggMasta on 2009-05-03
I tried doing the purge and reinstall thing, with the physically removing the directories said above, but no luck.

And I have libgpod4 and libgpod4-common installed in the synaptic package manager. I do not have libgpod4-nogtk (the one with no artwork support) or any of the others installed.

---

### Post by mc4man on 2009-05-03
Well I'd (taking note i don't use rhythmbox) would take a look at a couple of things
In rhythmbox -> edit -> plugins, try disabling some or all (except ipod) of the plugins (believe that may have been suggested, but revisit)
and maybe look at your audio output plugin (I don't use pulse on 8.10, can't help there

Alt+F2 then run
gstreamer-properties

---

### Post by Vostrocity on 2009-05-04
If it's really an emergency and you don't want to deal with the hassle of installing and setting up another media player, try [Floola]("http://www.floola.com/modules/wiwimod/"). It's the best iPod tool ever. It's a very lightweight no-installation cross-platform open-source :) tool that handles music/picture/video/text transfers back and forth between you iPod and PC. It fits your case quite well since it doesn't sync the files but simply manages transfering files manually. Once you figure out Rhythmbox you can go back to syncing.

---

### Post by EggMasta on 2009-05-04
I tried Floola and it gave this:

```
owner@owner-laptop:~/Desktop/Floola-linux$ sudo ./Floola
[sudo] password for owner: 
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
Segmentation fault

```

And I tried disabling all the non-ipod plugs on rhythmbox, but no luck.

---

### Post by mc4man on 2009-05-04
Too bad nothing seems to work (does rhythmbox work at all?

We take a much smaller ipod to job sites to use in a dock, so just use amarok to add and or remove 'albums' every once and awhile. As long as there are some decent tags it's quite simple ( I just do a 'transfer', takes about 20 secs per album (folder)

For Floola read here, sounds like your on a 64 bit install

[http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting](http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting)

look under the 'linux' drop down

---

### Post by neu2buntu on 2009-05-05
if you are still wanting to stick with rhythmbox install this package ```
sudo apt-get install libgpod-dev
``` ,also goto synaptic search rhythmbox and right click it and install the recommended and suggested packages and try rhythmbox again.... ,..i see the libgpod-dev package contains the include files and static library( this may help,.who knows?)

and another app to try that might get you up and running ```
sudo apt-get install gtkpod
``` here the screenshot of it....  :guitar:

---

### Post by EggMasta on 2009-05-05
I tried gtkpod, and that didnt work either. It has to be a problem with the ipod, maybe the ipod library is corrupted somehow? The programs cannot access the file list? I have noticed that since this problem started, the few songs I have on my ipod already have lost the album art.

---

### Post by neu2buntu on 2009-05-05
this is probably the case here and we are blaming the software!!!!   as i said in an earlier post if you could try a friends ipod in rhythmbox you will soon find out....   how about if you could erase the albums without covers (i think you said you can still mount the ipod) and try again

---

### Post by EggMasta on 2009-05-05
I borrowed my friend's ipod, and rhythmbox recognized it

---

### Post by EggMasta on 2009-05-09
bump

---

### Post by ramenite on 2009-07-21
*note--using Xbuntu guest with Windows 7 host

The only way I get my iPod to work, is if I make sure I have all ISO images ejected before I connect it to the virtual machine. For instance, you may have to eject the addons iso image.

But once that's done, it works fine. I use Rhythmbox regularly from my Linux guest to play songs from my iPod.

---

### Post by guilly on 2009-07-21
Last post for this thread was in may....

---

### Post by hypeiv on 2009-08-04
I had the same problem with my Ipod. It worked fine in 8.10 but in 9.04 if I plugged it in Rhythmbox would crash. If I tried to re-open it while the Ipod was plugged in it would crash again.

Today I plugged my Ipod into a windows computer running itunes and I got a pop up saying there was a new version of the Ipod software. It updated my Ipod to version 1.3 and now everything works fine in linux.

---

