---
title: "Slow guide when using firewire"
date: 2008-04-16
forum: Mythbuntu
---

### Post by dabneyd on 2008-04-16
So, I'm using the 8.04 beta, and I'm pretty satisfied with everything (which is says a lot about this project, considering I'm using a beta), but the one nagging problem I have is that the program guide is miserably slow when I'm using my DCT6200 connected via firewire. It doesn't matter what deinterlacer I'm using (yeah, I searched the forums and found the thread blaming the bob 2x deint). I also disabled the channel icons in the guide, but it's slow either way. Is this common behavior using firewire, or is there some configuration change I can make? Like I said I'm running 8.04 beta with all the latest updates (as of yesterday) on an Abit AN-M2HD with an Athlon X2 4200 and 2GB RAM. I'm using the onboard video with the restricted Nvidia driver installed. Any suggestions would be appreciated!

Thanks!

---

### Post by 4dognight on 2008-04-17
Is it slow, or does it seem to freeze and then open the flood gates and process all those backlogged key presses? Ever since I upgraded to .21 mine will randomly do the freeze up thing. I also tried the deinterlace and icon trick, but it still happens once in a while for me. One thing I did notice was , I had the 'monitor DVD' setting turned on. When I had verbose logging on I could see it looking for a DVD about evey 4 thousands of a second. The msg was scrolling like crazy in the log. I turned it off and it doesnt seem as bad. Im thinking it might have been in a tight loop checking for the DVD and preventing other processses from getting CPU time.

---

### Post by dabneyd on 2008-04-17
Well, here's the thing; I have 2 tuners. A Hauppauge 150 and the firewire tuner. The slow guide only happens when I'm using the firewire tuner. So for right now, I can use the guide if I switch to the 150.

---

### Post by 4dognight on 2008-04-17
when your using firewire , is it also playing back HD? How is your overall CPU usage while playing back from the firewire versus the 150?

---

### Post by jjuzwik on 2008-04-30
Hi All,

I also have a comcast DCT6200, connected as a single tuner via firewire.  This is on:

mythbuntu 8.04 final. 
Dell Vostro 400 C2D E6750 1GB ram



I had/have the slow guide problem whenever i was watching(previewing) an HD show, my processor would go through the roof (>90% constantly).  Thanks to some earnest googling, i realized it had everything to do with the TV Playback profiles, where mine was set to CPU++.  When i knocked it down to slim, the problem was gone.  The CPU+ playback profile does still 'ok' for me, but could be alot better.  The big issue here is the LiveTV preview window, which i assume is based on your playback profile.  

I wish there was an obvious/easy way for me to just completely disable the LiveTV preview window.  Normal TV playback is fine on CPU++.  I guess i can try to hack up the ui.xml theme file somehow...  

Does anyone know how i could easily disable the livetv preview?

---

