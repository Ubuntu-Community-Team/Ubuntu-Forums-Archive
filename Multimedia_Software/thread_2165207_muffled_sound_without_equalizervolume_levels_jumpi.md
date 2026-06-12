---
title: "muffled sound without equalizer/volume levels jumping with equalizer"
date: 2013-08-03
forum: Multimedia Software
---

### Post by charles2 on 2013-08-03
Hello, I am new to ubuntu, I've installed it recently and there is a problem with my sound. Ubuntu version is 12.04 LTS (64 bit) and computer is acer aspire v3-551g-10466G75Makk laptop.
Sound is muffled, like sound source is under blankets. Voices are like in the distance. I can clearly hear the difference between the sound in windows and the sound in ubuntu, especially in heaphones (the sound in speakers is affected too). It doesn't depend on program, I tried flash (youtube), rhythmbox and movie player. What I have already tried to solve the problem:
a) Updating from Ubuntu Audio Dev team PPA - nothing changed
b) Removing PulseAudio - nothing changed
c) Installing Realtek High Definition Audio Codecs - sound disappeared
d) Booting from Ubuntu 13.04 LiveCD (PulseAudio version 3.0) - sound is the same
e) Playing with alsamixer - nothing changed
The only thing that solved the problem was PulseAudio equalizer (I use Dolby Home Theater on Windows as equalizer) that I installed from here: [http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)
I know it's old and unsupported version but the new one (from here: [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)) brings crackling. The old one with "Soft" preset makes sound almost perfect but brings another problem: strange volume levels. Quiet sounds are... TOO quiet. For example, quiet beginning of the song. Or whispering. I have to to increase volume to hear these sounds, but when sound must increase just a bit I have to decrease volume because it's getting too loud. Example: [http://www.youtube.com/watch?v=34C41eEpM48](http://www.youtube.com/watch?v=34C41eEpM48)
In the beginning of this melody normal volume for me is about 60%. In the end it must be not greater than 40% or I lose hearing.
Problem wih volume appears only with equalizer enabled. When I disable EQ it's okay, but if I disable it the sound will become muffled. Here is some information that could be important.

sudo aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep "Audio":

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)

Right now I have almost clear system only wih updates from default repositories and proprietary driver for ATI graphics, I didn't change anything yet. I hope someone can write something that could solve this problem.

P.S. Sorry if something isn't clear after my explanation. English is not my native language.

---

### Post by Bucky Ball on 2013-08-03
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. 

I suggest, to avoid confusion and increase your chances of help, that you break this into two separate threads, both in ***Multimedia & Hardware.***, with descriptive thread titles. Leave this one with the audio stuff and change the title accordingly, cut, paste and edit accordingly the video stuff in a new thread here with a specific title. Good luck.

Attempting to fix two issues on the same thread generally creates a dog's breakfast. ;)

PS: For the audio issue, sounds like you might be taking a leap too far by installing and reinstalling. Have you actually got Pulse Volume Control installed??? That is where you control all this. Software Centre or Synaptics and install:

pavucontrol (or in a terminal 'sudo apt-get install pavucontrol')

Open it (Apps>Multimedia), go to 'Playback', play some music. You should see the stream from the music app you are using. Start experimenting with output devices there and under the 'Output' tab.

PPS: Everything you need for Pulse is in the repositories already. Forget Win mindset: ALWAYS look in the repos first as apps there are fully supported, known to be stable (at least in LTS releases in my experience) and updated for the life of the release, not the case with a .deb.

Only use external .debs, PPAs, etc. for something specific or not included in the repos. (I'm meaning in Software Centre or Synaptic Package Manager in effect.) No reason to install an outdated, obsolete EQ from a third-party. Depending on a couple of factors, you can have a perfectly functional system with most bells and whistles without ever leaving the repos actually.

---

### Post by charles2 on 2013-08-04
Hi, thanks for the replying. I did as you said, hope now everything is right.
About the sound. I have already tried Pulse Volume Control but forgot to mention it. There're not so many things I could change with this, only volume levels from left and from right. I attached the screenshot. The same is for the "Playback" tab. And I'm sure that audio is sent to the Built-In Audio Analog Stereo, not HDMI (there's an option in "Playback" tab, and when I move sliders, volume changes).

---

### Post by Bucky Ball on 2013-08-04
Make sure you are on the Playback tab. There should only be 'System sounds' and nothing else. Now open VLC, or whatever you use, and start a music track. Back to PVControl. There should now be a new stream in Playback with options.

Repeat, Playback tab and must have something playing for a stream to appear and adjust.

Try that. You won't achieve a lot by tweaking the Output tab with no music playing and nothing/less under the Playback tab. Need a playback stream under 'Playback' to see what's going on.

---

### Post by charles2 on 2013-08-04
Same thing. Only volume levels.

---

### Post by Bucky Ball on 2013-08-04
Hmm. I'm stumped.

---

### Post by phish3 on 2013-10-08
@Bucky Ball, you may want to try the built in one again, with the following changes:  Disable tsched by finding: [indent]load-module module-udev-detect[/indent] with [indent]load-module module-udev-detect tsched=0 [/indent]  in your default.pa file.  Do compare over a day or so and switch around to see if there's a difference.  Another thing I've noticed is that flash seems to be "that guy" that's causing the popping.  I've set my flash to default to the alsa sinks directly to bypass / mitigate the issue.  Another thing you could do is ensure no other programs are using the sink while a flash window is using it - one flash stream by itself with no other audio streams should work fine without issue.  pavucontrol will let you monitor connected streams.

---

### Post by Bucky Ball on 2013-10-08
> **phish3 said:**
> @Bucky Ball, you may want to try the built in one again

I'm not the OP. Not my issue. Everything fine here. I think you should be addressing your post to charles2. ;)

This thread is over a month without activity so don't think there's much to see here, anyway, unless charles2 still needs help. Wouldn't know.

---

