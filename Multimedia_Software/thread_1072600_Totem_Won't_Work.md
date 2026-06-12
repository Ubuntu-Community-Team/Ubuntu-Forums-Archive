---
title: "Totem Won't Work"
date: 2009-02-17
forum: Multimedia Software
---

### Post by suda on 2009-02-17
[SOLVED] I'm new to everything. Did a Wubi install of 8.10 Intrepid on my Acer Aspire laptop. Everything works great except the media player. Totem will not play my Netflix video DVD. The message I get is "An error occurred. Could not read from resource."

The first error I got said I had audio source problems and suggested two gstreamer downloads, which I downloaded. Still would not play the movie DVD. I read through the messages in this forum and did the libdvdcss2 package through synaptic manager. No go.totem will not play the DVD. Tried different media players and still can't watch the movie.

Also tried reinstalling through synaptic manager. Same, same. Any suggestions? I am not good on this Terminal stuff if I need to imput code.

Thanks for your help.

---

### Post by gandaran on 2009-02-17
if the DVD has menus totem-gstreamer won't play them (totem-xine can, totem-gstreamer can play dvd's with menus if you buy the fluendo gstreamer codecs) use another player, install mplayer, vlc or gxine, gxine is the best player for DVD's.

---

### Post by suda on 2009-02-17
Thanks, Gandaran. Here's what happened. I installed gxine using synaptic. Went through the wizard setup, and everything was checked to show it was working. The gui appears where it should in Sound and Video under Apps on the desktop, but it does not appear as an option after the Netflix DVD is inserted and the window opens asking how you'd like to open the DVD. So I opened gxine manually and selected the DVD. The following message appeared: "Error reading NAV packet." And what does that mean? How do I fix that? 

Is there any issue with having installed Ubuntu on the C drive where Windows Vista is parked? I guess another workaround is to just watch the DVD on Windows, but I really like Ubuntu and can't imagine this problem can't be solved.

s.

---

### Post by gandaran on 2009-02-18
do you have **libdvdread3**, **libdvdnav4** + libdvdcss2 installed?
see this [http://www.google.pt/search?hl=pt-PT&q=Error+reading+NAV+packet.&btnG=Pesquisa+do+Google&meta=&aq=f&oq=](http://www.google.pt/search?hl=pt-PT&q=Error+reading+NAV+packet.&btnG=Pesquisa+do+Google&meta=&aq=f&oq=)

---

### Post by suda on 2009-03-26
Sorry for the delay, gandaran. Yes, I have all those packages installed. Nada. 

I've done a lot of reading up on this since, and I do understand the encrypted DVD issue and the workarounds, etc., and I've tried multiple players, but all with the same results, except now I'm getting the audio, at least, but no video.

---

### Post by Fenris_rising on 2009-03-26
I can't offer specific help but mplayer and totem player have gone from working fine (all the medibuntu and other codecs were/are in place) to not working other than mplayer plays the audio track only.

BUT I installed _smplayer_ which, after setting the video to x11 and the audio to Alsa in it's general settings tab, worked fine. Played DVD's, AVI's, RMVP's and mpg's perfectly.

I also then found a problem with Amarok (which had worked fine) and had to change the 'autodetect' setting in the 'engine' tab to Alsa for amarok to play my music once again

I wonder if any of the above will help as I find it strange that all the players stopped working at the same time for no apparent reason and you seem to have the same problem at first glance. I am running 8.04

regards

Fenris

---

### Post by suda on 2009-03-27
Do you know that you are an absolute genius, Fenris? It works!!!!! Yea!!! I can now watch my videos. I LOVE it! And, now I'm going to check those other programs to see if the settings were the deal breaker. But I really like the gui of SMPlayer. Very cool.

Thanks, again.s.

---

