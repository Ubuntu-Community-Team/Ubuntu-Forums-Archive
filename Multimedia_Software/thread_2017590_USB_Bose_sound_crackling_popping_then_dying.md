---
title: "USB Bose sound crackling popping then dying"
date: 2012-07-05
forum: Multimedia Software
---

### Post by rabarrett on 2012-07-05
Hi, I've been trying to troubleshoot this issue for a while now.  Any help would be much appreciated.

I'm having trouble getting my Bose "Companion 5 multimedia speakers" working with my installation of Ubuntu 12.04 (link to Bose product here:  [http://www.bose.com/controller?url=/shop_online/digital_music_systems/computer_speakers/companion_5/index.jsp](http://www.bose.com/controller?url=/shop_online/digital_music_systems/computer_speakers/companion_5/index.jsp) ).

The issue seems to be low level (not just Ubuntu).

What happens:

When I boot into Ubuntu, I can get Rhythm box to play ok.  However, if I try anything else (an .avi file, a webpage, or Clementine player with mp3 files) I get crackling, popping, or choppy sounds.  If I move the mouse around, especially if it seems graphic intensive, the problem gets worse (more crackling noises).  The more taxing it appears to be, the more likely it is that the sound will just die altogether until I reboot.  For some reason the videos at [www.bloomberg.com](www.bloomberg.com) seem especially bad for it (my sound normally goes dead in under 45 seconds and won't work until reboot).
	-Both my desktop running Ubuntu 12.04 and my laptop (running the same) have the same crackling problem.


Troubleshooting so far:
-A friend of mine who knows linux well tried to solve it for me without any luck.  He took pulseaudio out of the equation, but still had the problem just using AlSA.  Among the many things he tried was adjusting the latency, but that didn't help either.
-I've also tried things like adjusting the USB device settings in the config file from -2 to -1 so that it will use my USB sound and I also commented out the lines that would stop that.  These don't do anything.  (That really seems like it's for someone who is getting no sound at all, so it's not surprising this won't work.)
	-My friend's laptop running his Archlinux could play my Bose USB speakers without any problems.  
-I also tried setting my daemon.conf file to use 6 channels (based on this [http://lotphelp.com/lotp/configure-ubuntu-51-surround-sound](http://lotphelp.com/lotp/configure-ubuntu-51-surround-sound) ) but that didn't work either.
-I recently used a DVD to boot into Ubuntu Studio 12.04 (because it uses a live audio kernel) and this happened:
	-I got perfect sound for a minute or two
	-When I started moving windows around while sound was playing, the sound died again.
-Perhaps more interesting:
	-There is a headphone out jack on the Bose system.  When I use it, the audio is perfect for all applications (even the deadly bloomberg.com videos with .avi playing at the same time and moving around windows).
	-Also, there is an audio-in jack on the Bose system.  I can use a male-to-male mini jack to go from my soundcard's output to the Bose input and then all sound works perfectly.
		-However, it still requires the Bose to be plugged in to USB, otherwise I lose all sound.

Any thoughts?  

Any suggestions for trouble shooting?  (Or any suggestions for somewhere else to post to solve this?)

Any logs or other files I can provide to help someone help me work this out?

Your help is much appreciated!

Rick

BTW:  I sometimes get people posting responses like "My Bose USB system works great with Ubuntu 12.04," without any more details.  Is there anything I should ask such people to narrow down my problem?  (It's kind of annoying to hear such a response because it doesn't help solve my problem.)

---

