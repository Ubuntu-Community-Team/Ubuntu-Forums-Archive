---
title: "Headphones won't mute internal speakers!"
date: 2008-05-23
forum: Multimedia Software
---

### Post by Toshibawarrior on 2008-05-23
Well guys, I've been searching these forums for about two weeks for a satisfactory solution to this problem. Whenever I plug my headphones in my speakers keep playing...

I have a Toshiba A135 S4527 with Realtek ALC861 sound card...

I've tried EVERYTHING! I've added the "snd hda-intel model=3stack" and tons of other lines to /etc/modprobe.d/alsa-base (one by one of course) and nothing worked.

I tried the more basic solutions like using the "headphone switch" on the volume control...and nothing...

I'm getting really angry with this, so please PLEASE someone help me!!!

If you need any more info to help me troubleshoot this just ask!...

Thanks in advance!:)

---

### Post by 47_MasoN_47 on 2008-05-23
I thought there was a hardware relay built in the soundcard that was supposed to handle that.  Most of mine even if you just plug in a 1/8" jack into the audio port the sound stops.  Did it work before you upgraded?

---

### Post by Steve413z on 2008-05-23
two possible solutions:
[http://ubuntuforums.org/showthread.php?t=740702](http://ubuntuforums.org/showthread.php?t=740702)
[http://ubuntuforums.org/showthread.php?t=495330](http://ubuntuforums.org/showthread.php?t=495330)


usually headphones mute the speakers via hardware (switch inside the jack), I'm not sure how you could solve this.

if it's enough of a problem, you could probably get a USB sound card like this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16829128002](http://www.newegg.com/Product/Product.aspx?Item=N82E16829128002) for your headphones

---

### Post by Toshibawarrior on 2008-05-23
Well I used to have Vista installed in this laptop...it had it by default, but I took that crap out and installed Ubuntu hardy heron...It's the only ubuntu distro I've used in this machine... :(
I have yet to try Steve's suggestions...

---

### Post by Toshibawarrior on 2008-05-23
OK I'm a noob to this whole Linux thing. I tried the suggestions found on the threads above, but I don't know how to compile ALSA drivers...in fact I don't know how to compile anything in Ubuntu. Any help with this will be greatly appreciated! 
:popcorn:

---

### Post by 47_MasoN_47 on 2008-05-23
You probably already have ALSA drivers installed.  All mine have installed them by default.  It's integrated pretty tightly with the kernel from what I understand.  I don't think it would be a good idea to mess with them IMO.

---

### Post by Toshibawarrior on 2008-05-23
Thanks for your quick replies! I followed some steps on one of the threads above and found a script to download, compile and configure the newest ALSA drivers...I had them but they were an old version. I ran that script and the newest drivers were installed. Now it kinda works, but I have to disable the "front" level to mute the speakers, which is a step forward since before the script I couldn't disable that level without losing the headphones sound. Anyways, I'd really like to know if there's some way to accomplish this automatically without having to disable the front on AlsaMixer...

I read that adding "snd-hda-intel model=<something mask>8=lenovo" (or something like that) enabled the PC to do the speaker-headphone conversion, but it doesn't...it just disables my sound card. So I'm stuck with the manual process. 

Anyways thanks for your help, and please let me know if there's any way to automate the process. :guitar:

---

### Post by Copter on 2008-05-29
Hello.

I confirm that adding
```

options snd-hda-intel position_fix=1 model=lenovo

```
to /etc/modprobe.d/alsa-base (and rebooting) did the trick on Toshiba Satellite A200 15I (aka Equium A200). Now after plugging headphones jack internal speakers mute properly. I can also unmute them by switching unmute on Front slider in alsamixer.

Using Ubuntu 8.04, 2.6.24-17-generic, ALSA driver 1.0.16 (preinstalled).

Thanks,
Copter

---

### Post by Toshibawarrior on 2008-05-30
Thanks a lot for your input Copter!...But sadly it didn't work for me...

My soundcard is a Realtek ALC861...and when I apply the code you said above it stays the same...both headphones and speakers sound. Any more info about this issue is still very appreciated!! I hope I cn fix this soon is driving me crazy, to have to mute the "front" everytime...:(

LOL by the way Copter I love you signature! :)

:popcorn:

---

### Post by Paresh on 2008-05-30
Will this work on a Toshiba Tecra A9?

lspci reports my soundcard as Intel 82801H (ICH8 Family) with a Realtek ALC262 chip

---

### Post by doorman on 2008-05-30
People, here's the solution for all kinds of sound cards:

[http://ubuntuforums.org/showthread.php?p=5080647](http://ubuntuforums.org/showthread.php?p=5080647)

we can now all sit back, eat our :popcorn: and listen to the movie sound out of our earphones only :)

hope this helps you all

cheers!

---

### Post by Toshibawarrior on 2008-05-30
HUM HALLELUJAH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

At long last I finally fixed it!!!!

At least it works "normally" now. I used Copter's suggestion again, and I discovered that on the very bottom of the "/etc/modprobe.d/alsa-base" directory was a hidden "options snd hda-intel model=3stack" so any other fix I tried was forced to fail because that one got down there (I still don't know how). 

Anyways adding the "position_fix=1 model=lenovo" fixed it! At least when I don't mute anything...I always used to mute the "master" and then plug in my headphones...but if I do that the "speaker-headphone madness" begins!
I just have to pause whatever I'm listening to and plug in my headphones without any muting at all and it shut the speaker off!

W00T-W00T!!!

At last I have an almost normal sound experience n Ubuntu!

Thanks to all of you who contributed to my cause!!!

You can feel free to keep posting other fixes, so that other people can solve their problems!!!

:guitar::guitar:

---

### Post by Paresh on 2008-06-03
Thanks doorman, That link works for me!

My Toshiba Tecra A9 has a Realtek ALC262 soundchip and this option worked for me

> options snd-hda-intel model=hp-tc-t5735

The only issue is that I have to manually mute the speakers using alsamixer, but that's no problem for me.

---

### Post by Adrian Quek on 2008-06-28
I had the same issue with a Compaq Presario v3000 (i.e. Headphones won't mute internal speakers). I googled around, but I couldn't find a post that seemed to be dealing specifically with my model. So I went out on a limb and tried the solution posted for Toshiba laptops. I added the following line to /etc/modprobe.d/alsa-base.
```

options snd-hda-intel model=lenovo
```

---

### Post by taszka-nn on 2009-12-18
I have a Lenovo Y530. I set the last line in 
```
etc/modprobe.d
```to 
```
options snd-hda-intel model=lenovo-ms7195-dig
```I rebooted and... I thought everything was just fine, but it's not. Internal speakers mute when I plug in earphones and the sound seems to be louder, but still something is wrong. Right after the system is turned on Amarok works great. Then I click "pause" on Amarok and play something on YouTube and it also works good. Then I return to Amarok, I click "play" and after one second of mute "playing" Amarok stops responding.
I'm not sure whether this is the right place to ask for help, but the flash-amarok issue started when i started fiddling with Alsa. Why can't I have both - headphones that cooperate with speakers properly and YT that cooperates with Amarok properely? :cry: What should I do now?

---

### Post by kamalarora2kin on 2010-07-10
You all guys are doing it in a very difficult and time comsuming way. 

follow this link and the post given by "**[COLOR="Blue"]marcobra[/COLOR]**"

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/90609](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/90609)

well dont even need to read that big thread and search through that, I would say "just install [COLOR="Blue"]**gnome-alsamixer**[/COLOR] and you will find the options. never install alsamixergui. 

i have lucid on HP Compaq dc7100 sff. this worked for me. 

good luck

---

### Post by emelce on 2011-01-06
fujitsu siemens computer with alc262 intel hda soundcard:


just add at the end of /etc/modprobe.d/alsa-base.conf 

options snd-hda-intel model=ultra


otherwise the laptop runs out of the box.

---

### Post by gejemur on 2011-07-31
Try this way:
System -> Preferences -> Sound -> Output
And change Connector value to Headphones.

---

