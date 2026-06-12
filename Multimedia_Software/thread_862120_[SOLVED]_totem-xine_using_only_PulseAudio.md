---
title: "[SOLVED] totem-xine using only PulseAudio"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Fibonacci on 2008-07-17
Hello,

I recently installed totem-xine. Now, whenever one or more apps (which I've gotten to cooperate using ALSA) produces sound, totem-xine produces none; and vice-versa, whenever totem-xine produces sound, all other apps are muted. Apparently this happens because totem-xine outputs sound through PulseAudio instead of ALSA, and I don't know how to change it to use ALSA.
I've also installed xine-ui, and configured xine to output sound through ALSA, which it does without a problem. This has no effect in the behaviour of totem-xine.

How can I configure totem-xine to use ALSA instead of PulseAudio?

Thanks in advance,

-Fibo

---

### Post by Melcar on 2008-07-17
If anything, Pulseaudio allows for multiple streams, and not the other way around.  Totem is probably using something else like OSS, or accessing your sound chip directly.  Also, it's weird that xine-ui does not change your xine parameters globally because it should; maybe if you try gxine instead?  Besides, why use Totem-xine and not just plain xine-ui or gxine? Totem works much better with gstreamer, and the recent GNOME builds integrate better with it as well.

---

### Post by Fibonacci on 2008-07-17
> **Melcar said:**
> If anything, Pulseaudio allows for multiple streams, and not the other way around.  Totem is probably using something else like OSS, or accessing your sound chip directly.

Whenever any application outputs sound through PulseAudio, no other app which uses ALSA directly can output sound - I've tested this. It's not that PA doesn't allow for multiple streams, it's just that it doesn't cooperate with ALSA.
Also, I'm 100% sure it's not using OSS or anything like that, since it doesn't open /dev/dsp like all other OSS apps do. 

> **Melcar said:**
> Also, it's weird that xine-ui does not change your xine parameters globally because it should; maybe if you try gxine instead?

Changes made in the xine-ui prefs affect gxine and viceversa. Neither affects totem-xine.

> **Melcar said:**
> Besides, why use Totem-xine and not just plain xine-ui or gxine?

Because, unlike gxine or xine-ui, totem-xine can be set as my default DVD player on Gnome.

> **Melcar said:**
> Totem works much better with gstreamer, and the recent GNOME builds integrate better with it as well.

totem-gstreamer cannot access the DVD menus, while totem-xine can. That's reason enough for me to ditch gstreamer.

---

### Post by markbuntu on 2008-07-17
You can fix the alsa/ pulseaudio conflict. I did it with:

asoundconf-gtk  (choose default alsa sound card)

and used it to chose pulseaudio as the default sound card for alsa.

You probably also need these to get this to work with oss, etc:

alsa-oss  (alsa wrapper for OSS apps)
alsa-utils  (command line utilities)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

I use vlc to play my dvd's. It is more configurable.

---

### Post by Fibonacci on 2008-07-17
> **markbuntu said:**
> You can fix the alsa/ pulseaudio conflict. I did it with:

asoundconf-gtk  (choose default alsa sound card)

and used it to chose pulseaudio as the default sound card for alsa.

You probably also need these to get this to work with oss, etc:

alsa-oss  (alsa wrapper for OSS apps)
alsa-utils  (command line utilities)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

Doesn't work for Flash (and yes I did try libflashsupport).

> **markbuntu said:**
> I use vlc to play my dvd's. It is more configurable.

VLC cannot access the root menu in most cases; plus it has this bug: [http://forum.videolan.org/viewtopic.php?f=13&t=48319](http://forum.videolan.org/viewtopic.php?f=13&t=48319) . None of that happens on xine.

---

### Post by markbuntu on 2008-07-17
Well, you need flash 10b to get over your flash problems. If you get flash 10, do not get flash10b2, it is very buggy but flash10b works great. Also, get rid of libflashsupport when going to flash 10, it will just cause problems.

I have had zero problems with vlc. It plays my dvd's and streamcasts just fine, no problems at all. Full screen dvd playback is great. I also like miro but other people seem to have problems with that also.

---

### Post by Fibonacci on 2008-07-17
> **markbuntu said:**
> Well, you need flash 10b to get over your flash problems. If you get flash 10, do not get flash10b2, it is very buggy but flash10b works great. Also, get rid of libflashsupport when going to flash 10, it will just cause problems.

That's why I don't want to switch to Pulse - I'd have to replace Flash 9 by 10b. I'd much rather get totem-xine output sound through ALSA instead of having to switch to PulseAudio just because of *one* unchangeable option in *one* app.

> **markbuntu said:**
> I have had zero problems with vlc. It plays my dvd's and streamcasts just fine, no problems at all. Full screen dvd playback is great. I also like miro but other people seem to have problems with that also.

What about root menus, which I mentioned in my previous post? Does it play the DVD exactly as a hardware player would? The only player I've found that does that is xine, which also has all the advantages you mentioned of VLC.

---

### Post by qrwe on 2008-07-18
I'm having this problem too: if I start Firefox and begin watching a movie at youtube, vlc stays silent. I have to close Firefox and after that restart vlc to get sound working again.
Are Fibonacci and I the only guys having this problem? This should have been a struggle even before they switched to PA instead of ALSA by default.

---

### Post by Fibonacci on 2008-07-18
> **qrwe said:**
> I'm having this problem too: if I start Firefox and begin watching a movie at youtube, vlc stays silent. I have to close Firefox and after that restart vlc to get sound working again.
Are Fibonacci and I the only guys having this problem? This should have been a struggle even before they switched to PA instead of ALSA by default.

VLC is easy to change to use ALSA: go to Settings -> Preferences -> Output modules, click on Advanced options, and change the audio output module to ALSA. What I'm looking for is a way to do the same in totem-xine.

---

### Post by markbuntu on 2008-07-19
> **Fibonacci said:**
> 

What about root menus, which I mentioned in my previous post? Does it play the DVD exactly as a hardware player would? The only player I've found that does that is xine, which also has all the advantages you mentioned of VLC.

VLC does that for me. I load the dvd, I open it with vlc, it plays. If I want the menu, I click a menu to get it, no problem. I really do not care if it exactly emulates my dvd player. I only care that it plays the movie and gives me the menu if I want it. In fact, the menu screen exactly emulates the dvd player menu screen but vlc skips that part and goes directly to playing the movie. 

Actually, I think this is an improvement over dvd players, put the disk in, the movie plays. No stupid menu unless I want it.

It is also easy to change vlc to whatever video and audio outputs, decoders, eq, whatever, I choose. It has an extensive preferences menu so it is easy to dial it in to my system for maximum performance.

xine crashes my system when I try to use it with Miro but gstreamer works just fine so I have learned to avoid xine as a general principle. Totem xone may work on my system and I have it, but why bother when I have other things that I know for sure work.

The best thing about Ubuntu and Linux is that it gives you choices. Something does not work the way you want, try some other stuff until you find something that does. The worst possible thing you can do is stubbornly insist that some thing should work some way when it obviously does not.

Have some popcorn....:popcorn:

btw, the flash problem with audio is due to bugs in flash 9 in the way it interacts with pulseaudio and the reason why libflashsupport was written in the first place, as a workaround for the inherent bad code in flash 9. Flash 10 fixes all that.

---

### Post by Fibonacci on 2008-07-19
> **markbuntu said:**
> VLC does that for me. I load the dvd, I open it with vlc, it plays. If I want the menu, I click a menu to get it, no problem. I really do not care if it exactly emulates my dvd player. I only care that it plays the movie and gives me the menu if I want it. In fact, the menu screen exactly emulates the dvd player menu screen but vlc skips that part and goes directly to playing the movie. 

Actually, I think this is an improvement over dvd players, put the disk in, the movie plays. No stupid menu unless I want it.

I do care if the root menu is the only place where I can choose between Cantonese and English; not only for the subtitles/audio, but for all the buttons in the DVD. No amount of clicking through VLC menus will take me to the DVD root menu in that case.

> **markbuntu said:**
> It is also easy to change vlc to whatever video and audio outputs, decoders, eq, whatever, I choose. It has an extensive preferences menu so it is easy to dial it in to my system for maximum performance.

Oh, sure it is. It's also easy on xine-ui. Only in totem-xine I haven't been able to do it.

> **markbuntu said:**
> xine crashes my system when I try to use it with Miro but gstreamer works just fine so I have learned to avoid xine as a general principle. Totem xone may work on my system and I have it, but why bother when I have other things that I know for sure work.

I've never ever had xine crash on me, and I've been using it since Fedora Core 4. GStreamer doesn't work just fine - it cannot access the DVD menus, it cannot jump to another chapter, and has serious problems skipping a large amount of time in the video. Xine does all that and so does totem-xine, that's why I'm so intent on making it work right.

> **markbuntu said:**
> The best thing about Ubuntu and Linux is that it gives you choices. Something does not work the way you want, try some other stuff until you find something that does. The worst possible thing you can do is stubbornly insist that some thing should work some way when it obviously does not.

Have some popcorn....:popcorn:

That's why I installed totem-xine to play my DVDs.

> **markbuntu said:**
> btw, the flash problem with audio is due to bugs in flash 9 in the way it interacts with pulseaudio and the reason why libflashsupport was written in the first place, as a workaround for the inherent bad code in flash 9. Flash 10 fixes all that.

Once again, I'd much rather get totem-xine to work than switch to Flash 10b. But apparently I have no other choice.

---

### Post by Fibonacci on 2008-07-25
I solved it.

To get ALSA sound output in totem-xine, I had to add the line "audio.driver:alsa" to the file ~/.config/totem/xine_config. However, I could not find that info on any manual anywhere - only experimentation got me there.

Thanks for the popcorn.

---

### Post by fauzie on 2008-09-01
This problem drives me crazy. Totem-xine is the only thing that can play VCD in my system (Hardy). But just like yours, it has no sound. If I use your solution of editing ~/.config/totem/xine_config I can get sound to work, but can no longer play VCD. 

Help please ....

---

### Post by fauzie on 2008-09-01
ok ... VCD works if I choose 

Open Location

and type in

VCD://


It won't run if I chose "Open CD"

So I put a new item in the menu that has launcher command:

totem-xine vcd://

---

