---
title: "Headphone Audio not working in 9.04"
date: 2009-04-29
forum: Multimedia Software
---

### Post by thisnamestoolong on 2009-04-29
I just installed Ubuntu 9.04 x64 on my Asus G50V laptop. I get sound fine out of my speakers, but no sound from my headphone jack. When I open up alsamixer, I can see an option for headphones but it will not let me turn the volume up on it. Any suggestions?

---

### Post by thisnamestoolong on 2009-04-29
After checking around a bit I see that in the Volume Control Preferences it is listing the headphone jack as a switch, not an output device. I figured that this could be relevant.

---

### Post by Ed Hunter on 2009-04-29
I am also having a problem getting my headhone socket to work, I am running 9.04 on a Sony Vaio VGN-AR51E Laptop. The socket works fine when using windoze but I have never been able to get it to work in ubuntu.

I can alter the volume control for Headphones but this has no effect.


Cheers

---

### Post by thisnamestoolong on 2009-04-29
I added the line

options snd-hda-intel model=g50v

to alsa-base.conf, but this seems to have had no effect. I can still see the headphones listed as a switch in volume control prefs. I really want to keep using Linux, but if I cannot use headphones I will have to go back to Windoze -- please help.

---

### Post by thisnamestoolong on 2009-04-29
Added the following to alsa-base.conf:

alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=g50v
options snd-hda-intel enable_msi=1

but still no solution in sight, I have also tried every combination of outputs I can possibly think of in Sound Preferences, but the same problems continue -- the speakers work, the speakers cut out as they should when I plug in headphones, but I cannot get sound from the headphones. Nothing is muted, all levels are at 100%. I need to have the headphones on this machine working for it to be a viable computer, please help!

---

### Post by thisnamestoolong on 2009-04-30
Sorry guys I hate to keep bumping but I really need to figure this out -- does anybody have any idea what I can do to fix this? I really am at my wit's end trying to figure it out and any help would be greatly appreciated.

---

### Post by crazy_fox on 2009-04-30
You have to active the Independed HP switch from the preferences and then select off.

Right click speaker icon
->Open volume control
->Preferences
->Enable Independed HP switch (second from last)
->close

Then click the Options tab, and set independed switch to "OFF"

---

### Post by Ed Hunter on 2009-05-01
> **crazy_fox said:**
> You have to active the Independed HP switch from the preferences and then select off.

Right click speaker icon
->Open volume control
->Preferences
->Enable Independed HP switch (second from last)
->close

Then click the Options tab, and set independed switch to "OFF"


I for one do n ot have the option described above: When I select volume control and then preferences all I am able to do is to select the visable tracks rather than turn any other option on or off.

---

### Post by tomsa on 2009-05-01
Please post the output of the following:

```
aplay -l
```

I have a hunch, but I may also be completely wrong.

---

### Post by Ed Hunter on 2009-05-01
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by tomsa on 2009-05-01
Well, the problem you're having is similar, but not the same as the one I'm having.  You might try some of the information from this thread:

[HTML]http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html[/HTML]

You might also want to see if your problem is at all related to this confirmed bug that affects those of us with a STAC9205 sound card.  

[HTML]https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/306755[/HTML]

Hopefully this will steer you in a useful direction.  I was hoping to have more to offer you, but unfortunately I don't.

---

### Post by thisnamestoolong on 2009-05-01
Ok the output of aplay -l is

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by crazy_fox on 2009-05-02
Ed Hunter,

What are the options in your preferences? What tracks can you enable?

---

### Post by yrrapm on 2009-05-02
I had a similar problem. I solved this by activating the Headphone Jack Sense switch in preferences. You need to then go to the Switches tab and check the tick box.

Hope this helps.

---

### Post by thisnamestoolong on 2009-05-02
Hey, I have tried all of that, I have the headphone option selected a switch, and have tried it on and off and neither one works.

---

### Post by minj on 2009-05-02
Try this:
*open volume control
*open preferences
*tick surround channel
*close preferences
*unmute surround channel
*be happy :)

---

### Post by thisnamestoolong on 2009-05-03
minj- I don't have any options for surround sound -- is this something that I need to enable in the config file? Also, the volume is fine coming out of the speakers so i dont think that a muted channel is responsible -- this is a tenacious little bug.

---

### Post by rwakc on 2009-05-03
Try inserting this line

options snd-hda-intel model=vaio

in alsa-base.conf and reboot your computer.
It worked in my case. I'm using vaio fz21z.

---

### Post by l1th1um on 2009-05-03
> **minj said:**
> Try this:
*open volume control
*open preferences
*tick surround channel
*close preferences
*unmute surround channel
*be happy :)

Thanks it works for me :guitar:

---

### Post by thisnamestoolong on 2009-05-06
Still having problems here -- I have since installed Ubuntu on 2 desktops with no such issues, using the x86 build rather than x64. Could this be part of the issue? If so, how much of a loss in performance will I see going from the x64 to x86?

---

### Post by alexwbaule on 2009-05-13
Did you make the headphone work ? 

My solution is come back to Ubuntu 8.10.

you find something different ?

I found 2 bugs about this, and no one have ansers.

[https://bugs.launchpad.net/ubuntu/+bug/368971](https://bugs.launchpad.net/ubuntu/+bug/368971)

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/374711?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/374711?comments=all)

---

### Post by arturvt on 2009-05-14
Hey guys, how ya doing?

Well I'm specting the same problem, I have an Asus G50VT and it was working fine at the 8.10 Ubuntu version but since the day that I've upgraded my SO to 9.04 I've lost my sound at the audio-out, no matter if it is an HEADPHONE or something else that receive sound. Just to know, if you put play and put your headphone you can hear something just a little sound? 


If you find something to help send me an email please! I hate use windowsVista...;)

---

### Post by arturvt on 2009-05-14
my email [email]arturvt@gmail.com[/email] 

:D

---

### Post by Billbrasky7718 on 2009-06-23
I am having the exact same problem with my gateway after i upgraded to 9.04 and the sound card is the

intel, stac92xx

i just upgraded the alsa driver to 1.0.20 as sugested in another forum but i keep reading about the surround option and turning it on but i cant locate anything like that..... any ideas??

---

### Post by Tinka on 2009-06-26
Hey guys, I don't use Ubuntu, but I came across this thread while trying to solve some problems with my Fedora 11 install. I ended up putting the line "options snd-hda-intel model=g71v" in the file "/etc/modprobe.d/alsa.conf" and rebooting. This got my headphone jack working properly on my Asus g50vt-x5. Good luck! Anyone know how to get the dvd burner working properly? lol :)

---

### Post by dimule4ka on 2009-07-12
> **Tinka said:**
>  I ended up putting the line "options snd-hda-intel model=g71v" in the file "/etc/modprobe.d/alsa.conf" and rebooting. This got my headphone jack working properly on my Asus g50vt-x5. Good luck!

Thanks, Tinka. It worked for me on Asus g50vt-x6

---

### Post by jorger53 on 2009-07-24
Thanks it works for my asus G50vt-X5

---

### Post by Duke.Augustine on 2009-07-25
I still have got some problems.  My computer is Acer 4736G.  Here is my step:
[LIST=1]
[*]I tried a test to detect my sound card
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
[*]And I also tried:
```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: LSI ID 1040

```
[*]So, I'm sure that my sound card is Realtek ALC888.  Then I edited /etc/modprobe.d/alsa-base.conf
```
$ sudo emacs -nw /etc/modprobe.d/alsa-base.conf
```
[*]Append the sentence below to the file:
```
options snd-hda-intel model=3stack-6ch
```
[*]Then I rebooted my laptop.  When it done, I couldn't believe that my laptop still cannot use headphone!
> In Volumn Control, I had toggled the headphone on.  Please do not tell me that alert.
Please~~Help~~
[/LIST]

---

### Post by Duke.Augustine on 2009-07-26
Solved!
Solved!
I solve it!

I referenced the page:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

[LIST=1]
[*]First, You can check whether your computer has been install build-essential and module-assistant, whether your linux header is updated, whether you has the alsa source.
```
$ sudo apt-get install \
build-essential linux-headers-$(uname -r) module-assistant alsa-source
```
[*]Use dpkg-reconfigure to reconfigure alsa-source
```
$ sudo dpkg-reconfigure alsa-source
```
[*]Now you have 2 ways to be access the success.
[LIST]
[*]One is through module-assistant:
```
sudo module-assistant a-i alsa-source
```
[*]The other is through manually compilation:
```
cd /usr/src
sudo tar xjvf alsa-driver.tar.bz2
cd module/alsa-driver
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) \
--with-cards=ALC888 \
--with-oss=yes
sudo make
sudo make install
```
> Note: "ALC888" in "--with-cards" can be replaced what sound card your computer has.
[/LIST]
If you don't have got any error message, congratulations!  Just reboot and enjoy it!
[/LIST]

---

### Post by cpbl on 2009-08-05
> **minj said:**
> Try this:
*open volume control
*open preferences
*tick surround channel
*close preferences
*unmute surround channel
*be happy :)

Super! I've been scratching my head on this for months (since 9/04!). That works.  Can anyone explain the logic!? What is "surround"?
Cheers
chris

---

### Post by ccorti on 2009-08-08
Hi,
My problem is similar; I hope someone could help. I have a Dell Dimension C521 w/ Sound Blaster Audigy MB. Although I have tried some of the suggestions on this thread, e.g., set playback to surround sound, still no headphone sound. 

aplay -l shows:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and I have Sound Preferences all set to ALSA, and Default Mixer Tracks, Device: HDA NVidia

Do I need to modify the alsa-base.conf in some way? 

Any help would be much appreciated.

---

### Post by netdevil on 2009-09-03
It really helped! Thanx a lot

---

### Post by Spkr2Cmputrs on 2009-09-11
> **Tinka said:**
> Hey guys, I don't use Ubuntu, but I came across this thread while trying to solve some problems with my Fedora 11 install. I ended up putting the line "options snd-hda-intel model=g71v" in the file "/etc/modprobe.d/alsa.conf" and rebooting. This got my headphone jack working properly on my Asus g50vt-x5. Good luck! Anyone know how to get the dvd burner working properly? lol :)

I own an Asus G50 series laptop, and I confirm that this works for this series.

---

### Post by ASCHYIEL on 2009-12-23
I want to confirm that adding 
options snd-hda-intel model=g71v
to the end of 
/etc/modprobe.d/alsa-base.conf 
works for my Asus g50vt-x2.

Thanks =)

---

### Post by stevepoppers on 2010-02-06
> **ASCHYIEL said:**
> I want to confirm that adding 
options snd-hda-intel model=g71v
to the end of 
/etc/modprobe.d/alsa-base.conf 
works for my Asus g50vt-x2.

Thanks =)

Worked for my friend's viao with model=viao instead of that.

---

### Post by Sporkman on 2010-02-22
> **Duke.Augustine said:**
> Solved!
Solved!
I solve it!

I referenced the page:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

[LIST=1]
[*]First, You can check whether your computer has been install build-essential and module-assistant, whether your linux header is updated, whether you has the alsa source.
```
$ sudo apt-get install \
build-essential linux-headers-$(uname -r) module-assistant alsa-source
```
[*]Use dpkg-reconfigure to reconfigure alsa-source
```
$ sudo dpkg-reconfigure alsa-source
```
[*]Now you have 2 ways to be access the success.
[LIST]
[*]One is through module-assistant:
```
sudo module-assistant a-i alsa-source
```
[*]The other is through manually compilation:
```
cd /usr/src
sudo tar xjvf alsa-driver.tar.bz2
cd module/alsa-driver
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) \
--with-cards=ALC888 \
--with-oss=yes
sudo make
sudo make install
```

[/LIST]
If you don't have got any error message, congratulations!  Just reboot and enjoy it!
[/LIST]

This broke my existing sound!!

Now my laptop has neither headphone nor speaker audio. :(

---

### Post by yax51 on 2011-03-09
Don't know if this will help, but in 10.10, with my Asus G50Vt I added this line to the end of alsa-base.conf and it worked great!

options snd-hda-intel model=asus-mode3

Hope this helps someone!!!

---

### Post by Duke.Augustine on 2011-07-19
> **Sporkman said:**
> This broke my existing sound!!

Now my laptop has neither headphone nor speaker audio. :(

I'm quite sorry about that.  But my solution is not an universe one.  At least it just works well on my laptop.

To your case, I guess if you have changed your kernel or something kernel modules that worked on old kernel well originally.

Maybe you can find the latest sound card driver and re-compile your kernel.

Good luck.

---

### Post by soultrip on 2011-09-16
> **Tinka said:**
> Hey guys, I don't use Ubuntu, but I came across this thread while trying to solve some problems with my Fedora 11 install. I ended up putting the line "options snd-hda-intel model=g71v" in the file "/etc/modprobe.d/alsa.conf" and rebooting. This got my headphone jack working properly on my Asus g50vt-x5. Good luck! Anyone know how to get the dvd burner working properly? lol :)

This worked for my Asus G50v running Mint 11 \\:D/

I've reinstalled mint 4 times trying a all sorts of fixes most which involved rebuilding kernels and inserting modules, all of which eventually broke my sound.  I should have known to check ubuntu forums **_FIRST_** ](*,)

THANK YOU TINKA!!!!

---

