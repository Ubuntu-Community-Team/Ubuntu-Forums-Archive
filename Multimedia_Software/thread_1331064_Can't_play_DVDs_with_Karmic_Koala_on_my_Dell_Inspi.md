---
title: "Can't play DVDs with Karmic Koala on my Dell Inspiron 6000 laptop"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Jahguin on 2009-11-18
Hi.  I installed Karmic Koala on my Dell Inspiron 6000 laptop and for the most part things have been great --- except for being able to play DVDs.  I'm clueless on how to start with diagnosing the issue and would love some assistance if someone would be so kind.

In a nutshell, if I put a DVD in the drive it appears to auto-mount and I get a "DVD" icon on my desktop which has a right-click Open with Movie Player option. Whether I use the right-click play option or launch Totem and then attempt to play, Totem appears to lock up after a short while --- though the process manager shows that the processor is not pegged (i.e. CPU < 5%).

Below are the steps I have tried.  After each step, I have tried playing DVDs with the same consistent behavior.

1. Installed Karmic Koala
2. Ran update manager and rebooted
3. Installed the restricted extras
4. Installed the Totem plugins
5. Rebooted 
6. Installed Kaffeine

Right now the laptop is a dual-boot with Win XP.  Playing DVDs works fine in Windows, but would love to remove Windows and just do Ubuntu.  Playing DVDs is the final hurdle.

Thanks in advance!

---

### Post by Jahguin on 2009-11-18
By the way, I started with the help steps from here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The "quick method" ran with no errors.  Not that I understand it, but below is what I did:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Then under the installation section I tried this:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

I got stuck in the terminal window with license info for java.  To be honest, I haven't been able to figure how to exit out of it.  Clicking the OK does not work, nor does hitting Enter or Ctrl-C or Ctrl-Z.

---

### Post by HappyFeet on 2009-11-19
```
sudo apt-get install libdvdcss2
```
enjoy

---

### Post by HappyFeet on 2009-11-19
> **Jahguin said:**
> 

I got stuck in the terminal window with license info for java.

There is a small box you need to tick on the left.

You can also do
```
sudo apt-get install sun-java6-plugin
```

---

### Post by bacchus123 on 2009-11-19
I can't offer much help to you because i am going through the same thing as you on this . 

I installed three different linux systems on my computer today and there are no other OS's on this Asus K50 laptop.  The three linux Distro's are: Mandriva 2010 , Ubuntu Ultimate edition 2.4 and ZevenOS 2.0 (Which is Built on Xubuntu). I really have no idea if this really matters or not in this situation . 

I am trying to get my dvd to play on ZevenOS first for no particular reason. Wireless, flash and sound all worked with no problems but , as the above has stated dvd is the last hurdle for me. 

I faithfully followed the sticky from ubuntu-freak " [all variants] Comprehensive multimedia
& video howto" but to no avail.

Can anyone please help with this?

To the above poster however, I can say that to exit the Sun certificate approval window, you must hit the alt key to highlight "ok" and then enter. That threw me for awhile too!:P

---

### Post by ilil on 2009-11-19
Can you play totem from Terminal? Then post here the text output (full with errors).

For example, if you have your DVD mounted in /media/cdrom then Applications menu -> Accessories -> Terminal and run command:
```

totem dvd:///media/cdrom

```
Now totem try to play DVD and output all messages to Terminal (post all them here).

Also, I recommend xine for DVD playing. Just install all xine with all codecs and package totem-xine. Then you can use totem with xine, 
```

totem-xine dvd:///media/cdrom

```

---

### Post by paulruscito on 2009-11-24
I've been struggling with the same problem all night.. I've tried the Medibuntu help page. I now have Movieplayer, mplayer, vlc and xine somewhat installed but none work. Seems like a codec is still missing but I don't know enough about this environment to fix this. Can anyone tell me a way to check and see if i have what I need on the system. This is so frustrating. I always have hope for Linux and I always fall short when I try to load it on a new machine. 

BTW, I am doing this on a Dell E6400 and I am surprised that I got the wireless networking working.

Thanks,
Paul

---

### Post by ilil on 2009-11-24
to paulruscito
Can you run totem in Terminal as I described at [http://ubuntuforums.org/showpost.php?p=8348729&postcount=6](http://ubuntuforums.org/showpost.php?p=8348729&postcount=6) ? What is the output?

---

### Post by jhenager on 2009-11-24
> **ilil said:**
> Can you play totem from Terminal? Then post here the text output (full with errors).

For example, if you have your DVD mounted in /media/cdrom then Applications menu -> Accessories -> Terminal and run command:
```

totem dvd:///media/cdrom

```
Now totem try to play DVD and output all messages to Terminal (post all them here).

Also, I recommend xine for DVD playing. Just install all xine with all codecs and package totem-xine. Then you can use totem with xine, 
```

totem-xine dvd:///media/cdrom

```
Having the same trouble, but my player window just closes.
jeff@jeff-desktop:~$ totem dvd:///media/cdrom
Segmentation fault

---

### Post by ilil on 2009-11-24
to jhenager
Hmm ... it's a bug, really :). The best you can do is to file the bug report to launchpad.net (about segmentation fault), and point out what source you try to play (DVD name, if it matters). 

Also try to check:
[LIST]
[*]try totem-xine instead of totem
[*]check if /media/cdrom is correct path for you (output of the command 'mount' in Terminal helps)
[/LIST]

---

### Post by jhenager on 2009-11-24
> **ilil said:**
> to jhenager
Hmm ... it's a bug, really :). The best you can do is to file the bug report to launchpad.net (about segmentation fault), and point out what source you try to play (DVD name, if it matters). 

Also try to check:
[LIST]
[*]try totem-xine instead of totem
[*]check if /media/cdrom is correct path for you (output of the command 'mount' in Terminal helps)
[/LIST]
Thanks, ilil.
Tried xine too. Path is correct. At least I have several OSs and one of them works...

---

### Post by paulruscito on 2009-11-28
OK, I'm giving all this a shot today. I'll post if it gets solved.

Thanks,

Paul

---

### Post by IzNohGod on 2009-11-28
Also had this problem on my Inspirion 6000. Ain't sure what i did, but everything works perfectly with vlcplayer and other media players. I belive my problem was the restricted drivers. I can try figure it out, and post later.

Also have some issues with my flash in Mozilla. The flash videos hangs after awhile. Read something about the Visual Effects(also known as Compiz) on ubuntu, can couse chace flow. Changed the option to "none visual effect" (System->Preferences->Apperance->Visual Effect), and will see if that turns out to be correct.


My solution was:
Installed restricted drivers
and install libdvdcss2 (for encrypted dvds)

---

### Post by lynne1949 on 2009-12-04
> **Jahguin said:**
> Hi.  I installed Karmic Koala on my Dell Inspiron 6000 laptop and for the most part things have been great --- except for being able to play DVDs.  I'm clueless on how to start with diagnosing the issue and would love some assistance if someone would be so kind.

In a nutshell, if I put a DVD in the drive it appears to auto-mount and I get a "DVD" icon on my desktop which has a right-click Open with Movie Player option. Whether I use the right-click play option or launch Totem and then attempt to play, Totem appears to lock up after a short while --- though the process manager shows that the processor is not pegged (i.e. CPU < 5%).

Below are the steps I have tried.  After each step, I have tried playing DVDs with the same consistent behavior.

1. Installed Karmic Koala
2. Ran update manager and rebooted
3. Installed the restricted extras
4. Installed the Totem plugins
5. Rebooted 
6. Installed Kaffeine

Right now the laptop is a dual-boot with Win XP.  Playing DVDs works fine in Windows, but would love to remove Windows and just do Ubuntu.  Playing DVDs is the final hurdle.

Thanks in advance!

Sorry but !! download Linux Mint Helena every thing works out of the box
Mint is based on top of Karmic Koala and comes with the codecs...

Lynne

---

### Post by ilil on 2009-12-04
to jhenager
I've found out that totem-xine is [not supported now](http://www.hadess.net/2009/05/era-comes-to-end.html), in Karmic. So, you should try pure xine player.
Just install xine-ui package.

---

### Post by Jahguin on 2009-12-29
Hi everyone.  Original poster here.  Sorry for the belated thanks, but I just installed a fresh, new install of Koala and have the "recipe" doe getting my Dell Inspiron 6000 laptop working with DVD playbacks.

Below is what I needed to do:

Step 1 - Installed Karmic Koala
Step 2 - Run update manager, download and apply all updates and reboot
Step 3 - Installed the restricted extras
Step 4 - Install the java6 plugin
4a - Open up a terminal window (Applications -> Accessories -> Terminal), 4b - Paste the below, hit Enter, type your superuser password and hit Enter again:

sudo apt-get install sun-java6-plugin

Step 5 - Add Medibuntu as a repository for downloads
5a - Open up a terminal window (Applications -> Accessories -> Terminal), 5b - Paste the below, hit Enter, type your superuser password and hit Enter again:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Step 6 - Install the libdvdcss2 library
6a - Open up a terminal window (Applications -> Accessories -> Terminal), 6b - Paste the below, hit Enter, type your superuser password and hit Enter again:

sudo apt-get install libdvdcss2

Step 7 - If you have a DVD already in your player, either eject and then reload or unmount and remount.

Step 8 - Play the DVD and have fun.


A few observations:
1. After steps 1-3 DVD playback just fails.
2. After step 4 the player crashes after attempting playback
3. After step 5 the player the player appear to lockup and not recover.  I had to kill the process a couple of times.
4. After step 6, I had to unmount and remount in order to work, hence my to-do in step 7.  Without ejecting/unmounting, the player locked up --- though the lockup appears, visually, different than after step 5.

Anyhoo, I am very thankful I can now play DVDs and am grateful for the free, helpful advise from many.  Thanks!

P.S. Anyone know a sane reason why medibuntu is not a available repo for software software, by default?  I can perhaps understand not having medibuntu enabled by default.

---

