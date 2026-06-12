---
title: "Headphones problem on Toshiba Sattelite"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by Aliosha on 2007-02-06
Hi, all

 I'm trying to fix the following problem and I hope I can get some help from you guys.

I installed Edgy on my Toshiba Sattelite A120 laptop. 

When I plug in the headphones the main speakers do not mute. I played a lot with the alsa controllers. I even installed the latest drivers for HDA Intel (posted on their website a few days ago) but i'm still facing the same behaviour...


Thanks

---

### Post by Richard Kut on 2007-02-07
Hello! You did not mention if you are using Kubuntu or not. The reason I raise the question is because the mixer panel applet in Kubuntu has an option hidden on one of the tab pages that can enable headphone sensitivity. At least that's what I think the feature is called, since I am not in front of my Kubuntu box right now. 

I had the same problem on my HP laptop, and enabling this feature allowed the laptop to realize that the headphones were plugged, and then muted the external speakers.

Have a look around the mixer applet in Kubuntu, if that is the variant that you are using. I cannot be sure, but I believe that the mixer in Ubuntu might have a similar feature.

Please update this post once you do figure out exactly how to fix the problem so that others may benefit too. Thanks, and good luck!

---

### Post by Aliosha on 2007-02-07
I fixed it, finally. i installed the last version of alsa as explained here: [http://www.jasin.biz/articles/2006/12/19/travelmate-2440-ubuntu-sound-problem](http://www.jasin.biz/articles/2006/12/19/travelmate-2440-ubuntu-sound-problem)

Although that was not all. I started alsa mixer and I played with the options for the headphones. I finally managed to get to the following:

headphones on: speakers off
speakers on: headphones off 

so the switch is controlled by software, if I may explain it this way. kind of weird but anyhow....

So for all who are experiencing the same problem: you may have just to start alsamixer and play around until you get sound to your headphones. if you expect this to happen by pluggin the headphone only you may be wrong..


Thanks

PS: i'm not using kubuntu

---

