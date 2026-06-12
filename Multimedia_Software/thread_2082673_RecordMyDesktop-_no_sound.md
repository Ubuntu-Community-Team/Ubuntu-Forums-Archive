---
title: "RecordMyDesktop- no sound"
date: 2012-11-10
forum: Multimedia Software
---

### Post by PDA1 on 2012-11-10
I'm running Ubuntu 12.04

In using RecordMyDesktop (RMD), while watching a video online, no sound is recorded.

In the RMD sound Device is set as "default"

aplay -l output is;

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any idea how to fix this from someone who has actually done it?

---

### Post by Halbblutplins on 2012-11-10
Use "pulse" instead of "default".

And then install pavucontrol with:

```
sudo apt-get install pavucontrol
```This mixer gives you then the posibility to change the device from which RMD shall record.


Peter

---

### Post by PDA1 on 2012-11-10
That worked perfectly!

Thanks!

The other problem is that after about 5 seconds into the playback of the record desktop, all motion within the video ends. Playback still continues with the sound playing very well but there's no video movement. (I'm trying to copy an earthcam video feed).

---

### Post by Halbblutplins on 2012-11-10
Yeah I know that ...

... click the button for advanced settings. Go to the performance options (don't know the correct words because I'm German &#8594; I have the german version) and activate all options instead of the first one, something like "encode while recording" because this will speed up your video and make a for example 5min recording to a 5s video. Furthermore you should create a new folder which you use as "work directory" in the advanced settings.

By the way: You should try Kazam, just search in the software center.


Peter

---

### Post by PDA1 on 2012-11-10
Kazam doesn't work.

It doesn't allow for any kind of  select region...even though there's the option of it.

---

### Post by Halbblutplins on 2012-11-10
Normally Kazam shall show a rectangle which you can resize and then you would press enter and click on start ..... do you use normal desktop environment so Unity or other like Lxde? Because on Lxde this function doesn't work.


Peter

---

### Post by cybrsaylr on 2012-11-10
> **PDA1 said:**
> Kazam doesn't work.

It doesn't allow for any kind of  select region...even though there's the option of it.

Kazam works the best for me. It does have a rectangle to select region what you want. The only problem I have is the color is too green and I don't know how to correct the color.

Running 64bit 12.04 with Unity, I have: Kazam Screencaster - "NCC-2893" 1.0.6 version.

---

### Post by PDA1 on 2012-11-10
I'm running Gnome-Desktop instead of Unity. ('Pretty sure that's what it's called...regardless I'm not using Unity).

'Can't select any region or area. Kazam dialog just sort of goes "gray" and does nothing.

Thanks for trying.

---

### Post by Halbblutplins on 2012-11-10
Using unstable ppa fixes the colour bug:

Open terminal and type in:

```
sudo apt-get remove kazam
```then add the ppa by typing in:

```
sudo add-apt-repository ppa:and471/kazam-daily-builds
```then this one **(really important!)**:

```
sudo apt-get update
```and finish by using this command:

```
sudo apt-get install kazam
```**Have fun!**


Peter

---

### Post by Halbblutplins on 2012-11-10
> **PDA1 said:**
> I'm running Gnome-Desktop instead of Unity. ('Pretty sure that's what it's called...regardless I'm not using Unity).

'Can't select any region or area. Kazam dialog just sort of goes "gray" and does nothing.

Thanks for trying.

If you can, try on Unity.

If this doesn't help I have an other programm for you:

FFmpeg

It's a commandline tool which is really powerful.

Here's is an example you could try:

```
ffmpeg -f x11grab -s ****x**** -i :0.0 -r 30 -qscale 1 -vcodec mpeg4 /home/******/video.mp4
```I explain ... 

- "ffmpeg" &#8594; programm;
- "-f x11grab" &#8594; just don't change;
- "-s" &#8594; Resolution &#8594; put instead the * the resolution you want for example "1920x1080";
- "-i"&#8594; just don't change;
- "-r" &#8594; framerate;
- "-qscale"&#8594; quality &#8594; from 1-30 (30 is bad);
- "-vcodec" video codec; the rest &#8594; direcory where to safe &#8594; put instead * your username

**important!:**

If you wanna record only a region use an other syntax for resolution option "-r".
Use instead of "****x****" &#8594; "   ****x****+'''',''''    "

****  &#8594; which size the region have
'''' &#8594; 1. is X-coordinate and 2. Y-coordinate

**-----------------------------------------------------**

but before you have to install ffmpeg:

```
sudo apt-get install libav-tools
```
Peter

---

### Post by cybrsaylr on 2012-11-11
> **Halbblutplins said:**
> Using unstable ppa fixes the colour bug:

Open terminal and type in:

```
apt-get remove kazam
```

then add the ppa by typing in:

```
add-apt-repository ppa:and471/kazam-daily-builds
```

then this one **(really important!)**:

```
apt-get update
```

and finish by using this command:

```
apt-get install kazam
```

**Have fun!**


Peter
I usually have no problems putting code in terminal but this is what I'm getting after putting, 
> apt-get remove kazam 
in terminal as you suggest.

> rr@rr-Studio-XPS-8000:~$ apt-get remove kazam
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
rr@rr-Studio-XPS-8000:~$ 


What am I doing wrong?
It doesn't ask for a password.



BTW I removed Kazam using Synaptic Package Manager.

---

### Post by Halbblutplins on 2012-11-11
Oh sorry i forgot to add one aspect. You have to be sudo.

Just put before every command a "sudo". Then he asks for password and will start installing/...

example:

```
**sudo** apt-get remove kazam
```

*Update: updated old posts, just copy paste


Peter

---

### Post by cybrsaylr on 2012-11-11
Yeah figured 'sudo' has to be added to code somehow. I use terminal but am not real strong at command line.

Anyways I used all your codes from your above post #9 Halbblutplins and it now did what was expected. Then I opened up Kazam and did another 'test sample' and the results were the same as before. Kazam copied a YouTube clip very well but color was still off and very green. Color was not corrected at all.

Any idea why color is still not accurate?


BTW just checked and I now have: Kazam Screencaster - "NCC-2893" 1.0.6 version, the exact same version I had before when using Synaptic for the install.

---

### Post by Halbblutplins on 2012-11-13
Errrrr ... I've no idea anymore.

But I can report as bug ... If I've time I'll do that.


Peter

---

### Post by cybrsaylr on 2012-11-13
Thanks Halbblutplins.

---

### Post by Halbblutplins on 2012-11-13
Yeah no problem ... !

But i need some informations about your system:

- OS/persion?
- processor?
- graphic card/driver?
- kazam version? (open kazam &#8594; tab "about")
- errr ... that's all

Mybe you can upload a video made with kazam on youtube or mediafire, .... or send me via skype (my skypename ..... guess!?!?! ..... "halbblutplins") so that they can see it. If I could make a video/record I would but I've desrtoyed it by installing graphiccard drivers again and again and ..... and again and again!  :/


Peter

---

### Post by cybrsaylr on 2012-11-14
Halbblutplins, system info you requested: 
[IMG]http://s12.postimage.org/6pfd5hs3v/image.png[/IMG]

Here's the YouTube clips.
First one was the source.
Second on was Kazam screencast sample:
1. [http://www.youtube.com/watch?v=vd9qM0sMC6E](http://www.youtube.com/watch?v=vd9qM0sMC6E)
2. [http://www.youtube.com/watch?v=5u4fzjaTbvc](http://www.youtube.com/watch?v=5u4fzjaTbvc)

Another pair here.
First source, second Kazam screencast sample:
1. [http://www.youtube.com/watch?v=YjqHkwHTRPY&feature=my_favorites&list=FL0fUBZK4Iqm6nOjipDLO69Q](http://www.youtube.com/watch?v=YjqHkwHTRPY&feature=my_favorites&list=FL0fUBZK4Iqm6nOjipDLO69Q)
2. [http://www.youtube.com/watch?v=4HpnzZWvak4](http://www.youtube.com/watch?v=4HpnzZWvak4)

Made this interesting discovery. Kazam uploads to YouTube have normal color of my original too green Kazam screencasts.
Oddly the Youtube Kazam screencast uploads look to have normal color while my original Kazam screencast copies have too much green!
Have no idea why? It is like YouTube corrected the color.

---

### Post by dannyboy79 on 2012-11-14
> **cybrsaylr said:**
> Yeah figured 'sudo' has to be added to code somehow. I use terminal but am not real strong at command line.

Anyways I used all your codes from your above post #9 Halbblutplins and it now did what was expected. Then I opened up Kazam and did another 'test sample' and the results were the same as before. Kazam copied a YouTube clip very well but color was still off and very green. Color was not corrected at all.

Any idea why color is still not accurate?


BTW just checked and I now have: Kazam Screencaster - "NCC-2893" 1.0.6 version, the exact same version I had before when using Synaptic for the install.if you are trying to save a video that you found on youtube just use a website called keepvid.

---

### Post by cybrsaylr on 2012-11-14
> **dannyboy79 said:**
> if you are trying to save a video that you found on youtube just use a website called keepvid.

Thanks but I know about keepvid and have used it in the past. It works great. I was just using YouTube for convenience sakes in those above clips.

---

### Post by Halbblutplins on 2012-11-14
Ok ....... that's creepy :/

Have you tried an other codec in Kazam?

Or just try to convert with Avidemux (just search in software center). In Avidemux you've to use (you don't have to but it's the one with smallest file size but really good quality) codec "MPEG4-AVC" and audio ... errr .... try "AAC" and the 3 aspect, instead of "AVI", "MP4" and then click save button and it will start converting. Maybe this will help .... ?


Peter

---

### Post by cybrsaylr on 2012-11-14
> **Halbblutplins said:**
> Ok ....... that's creepy :/

Have you tried an other codec in Kazam?
No.
Didn't know you could do that, or how to for that matter.


Will look into Avidemux.

---

### Post by cybrsaylr on 2012-11-18
Think I solved the color correction problem.
Surprised I didn't think of this sooner....:redface:

When I click on a Kazam screencast clip, Totem Movie Player opens the clips by default and originally all clips had too much green.

With Totem Player I just clicked on Edit > Preferences > Display and played around with 'color balance' settings just as you would do with any color TV, to make the color more natural and accurate as was the original clip.

---

### Post by cybrsaylr on 2012-11-22
A little follow up on Kazam.

Installed Kazam on a Dell core2 duo laptop and it runs great with no color problems. Color on laptop was very accurate. It must be something in my Dell desktop has to be corrected with the color settings in Totem Player to get accurate color.

---

