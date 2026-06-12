---
title: "Color problems and streamtuner in 8.04"
date: 2008-08-27
forum: Multimedia Software
---

### Post by RedRat on 2008-08-27
Two things:
I thought I had resolved a perplexing color issue. When I use totem to play a video, I get an almost b&w picture with tints of blue and green. Color is way off. If I quit and try to play the same video in VLC same thing happens. In order to get rid of this annoyance, I have to restart/reboot and then play the video with only VLC. Totem seems to have done something within the system to throw all video colors off. I note that others seem to have this same issue, I not alone.

I noticed that since upgrading to 8.04, xmms does not seem to be available. In Synaptic when I search for xmms, it comes up but there is nothing to download. Attempts to run streamtuner, in order to listen to internet radio gives an error:
Unable to tune in
Failed to execute child process
"xmms" (no such file or directory)

I note that my version of streamtuner is the same as in the synaptic repo. 

Any ideas on any of these??????

---

### Post by markbuntu on 2008-08-27
If you want xmms back and are using i386 you can get the debs here:


[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

If you are on amd64, the debs are here:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

---

### Post by RedRat on 2008-08-27
> **markbuntu said:**
> If you want xmms back and are using i386 you can get the debs here:


[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

If you are on amd64, the debs are here:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

Thanks for the http. However, what I find is that in 8.04 there is an installation of xmms2. It appears that it is streamtuner that seems to be out of whack with the newer xmms2. I do have an xmms2 directory and can indeed run xmms2 from the command line. Does anyone know what the deal is with streamtuner??

A quick perusal of streamtuner preferences indicates that it makes a call to xmms so that is the reason for the error. I also note that the streamtuner web page does not appear to have been touched since 2004 when the last build of the streamtuner program was made. It would appear that Ubuntu has passed it by. My guess is that streamtuner is no longer supported by those who developed the program.

As to using xmms or xmms2, I use Amarok for listening to internet radio so I really don't need streamtuner, but I thought it odd. It actually was a very nice lightweight program.

---

### Post by markbuntu on 2008-08-27
I still use streamtuner and xmms, xmms2 did not work with streamtuner, neither did audacity. That's why I hunted down the xmms debs. I run it through a pulseaudio/jack connection so I can add effects/eq/compression and record/playback with a few clicks.

I like them, they are a lightweight and easy combination. I also use tunapie sometimes with rythmbox but it does not have as many stations and loads up rythmbox with 20 channels when I only want one. I think I tried amarok once.

Anyway, I heard a rumor of a new streamtuner making its way through debian.

---

### Post by RedRat on 2008-08-27
> **markbuntu said:**
> I still use streamtuner and xmms, xmms2 did not work with streamtuner, neither did audacity. That's why I hunted down the xmms debs. I run it through a pulseaudio/jack connection so I can add effects/eq/compression and record/playback with a few clicks.

I like them, they are a lightweight and easy combination. I also use tunapie sometimes with rythmbox but it does not have as many stations and loads up rythmbox with 20 channels when I only want one. I think I tried amarok once.

Anyway, I heard a rumor of a new streamtuner making its way through debian.

OK great news in a new streamtuner comes in. I will look for it. Although when I went to the streamtuner page, I didn't see anything about a new version--but I didn't look all that closely. I'll keep my eyes open.

Thanks for the info.

---

### Post by markbuntu on 2008-08-28
It was just something I noticed once at launchpad, something about updating Ubuntu to new streamtuner from debian...very obscure...and I only saw it that once.

---

### Post by mcduck on 2008-08-29
Streamtuner works with just about _every_ music player you can find. It just has xmms as default setting since it used to be very common player on Linux systems.

It just happens to be that xmms is so badly outdated now that it was dropped from ubuntu's repositories. (since xmms there has been BMP, Audacious, BMPx and XMMS2, all more or less followers of xmms).

Just change the setting in Streamtuner's configuration to use the player you like best. (The reason why you couldn't get xmms2 to work is most likely that you used only the name of the program as the command, when you really need to include the variable that points to the stream, "%s" if I remember right.. Without that the command will only start the player, without telling it what to play.)

---

### Post by markbuntu on 2008-08-29
> **mcduck said:**
> Streamtuner works with just about _every_ music player you can find. It just has xmms as default setting since it used to be very common player on Linux systems.

It just happens to be that xmms is so badly outdated now that it was dropped from ubuntu's repositories. (since xmms there has been BMP, Audacious, BMPx and XMMS2, all more or less followers of xmms).

Just change the setting in Streamtuner's configuration to use the player you like best. (The reason why you couldn't get xmms2 to work is most likely that you used only the name of the program as the command, when you really need to include the variable that points to the stream, "%s" if I remember right.. Without that the command will only start the player, without telling it what to play.)

Well, that has not been my experience with streamtuner. XMMS2 would start but not play, audacious would try to start and then crash. I never even heard of BMP or BMPx. I got xmms and have had smooth sailing ever since.

I think dropping xmms was more of a political decision than anything else and keeping streamtuner without even changing its default player... :lolflag:

Anyway, if xmms is so deprecated, why are there new xmms builds for Ubuntu Hardy in launchpad?

---

### Post by mcduck on 2008-08-30
I just tried it, installed Streamtuner, set the commands in Streamtuner settings to start "audacious %q" instead of "xmms %q" and it works..

If that doesn't work for you check Synaptic if you are missing any Audacious plugin that might be important.

---

### Post by gandaran on 2008-08-30
> **RedRat said:**
> Two things:
I thought I had resolved a perplexing color issue. When I use totem to play a video, I get an almost b&w picture with tints of blue and green. Color is way off. If I quit and try to play the same video in VLC same thing happens. In order to get rid of this annoyance, I have to restart/reboot and then play the video with only VLC. Totem seems to have done something within the system to throw all video colors off. I note that others seem to have this same issue, I not alone.

I noticed that since upgrading to 8.04, xmms does not seem to be available. In Synaptic when I search for xmms, it comes up but there is nothing to download. Attempts to run streamtuner, in order to listen to internet radio gives an error:
Unable to tune in
Failed to execute child process
"xmms" (no such file or directory)

I note that my version of streamtuner is the same as in the synaptic repo. 

Any ideas on any of these??????

about the color problem, have you fixed it?
if not, then open totem » edit » preferences » screen tab, set the color of your choice.

---

### Post by RedRat on 2008-11-29
> **gandaran said:**
> about the color problem, have you fixed it?
if not, then open totem » edit » preferences » screen tab, set the color of your choice.

Sorry about the intervening months, but other things called. No I have not fixed the color issue. Here is the thing, even if I start totem by calling it from the command line, that mere act of calling it up screws up the color on all other video (avi, mpg, wmv) players. Now I took your advice and started Totem, then loaded a video and adjusted the color (basically pushing the hue slider all the way to the right) and then stopped Totem and then started VLC player with the same video, and indeed that worked, the video was "normal".

Any idea why that ought to be the case?? Two separate applications, yet one controls the color in the other? Very odd that they are linked.

---

