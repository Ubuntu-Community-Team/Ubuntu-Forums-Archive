---
title: "Sound Issues"
date: 2012-05-05
forum: Multimedia Software
---

### Post by WarDogLRS on 2012-05-05
[B]After a clean install i booted for the first time to ubuntu 12.04 the sound didnt work at first but after some fine tuning on the settings it was working fine and i was proud BUT then it happened the next day i booted & the sound was gone and now I have no idea where to look or what to do. 

I tried Alsa & checked Mute I dare not go to far without some advise

I went through this with Zorin & Bodhi after hours and hours of trying to get the sound to work i formatted the system and installed 12.04 over XP Pro

Is there anything for this issue seems simple to me I never had so much trouble for a simple sound card?

Is there a break down procedure so as to not mess it up with all those command lines & find out what is needed. 
Thank you for your help
[/B]

---

### Post by Curtis6767 on 2012-05-05
Do you have a dedicated sound card?

Have you installed Pulse Audio Volume Control?

It's in the software center.

With PAVC, you'll have options to select your current sound driver. I don't have a sound card so it uses Built-in Audio Analog Stereo.

To get to that window, you'll need to have some audio running. I set mine up with Rhythmbox and Audacity. 

Once you have audio running, then you open PAVC and click the tabs.

The image below is of my Playback tab. To set up the Recording tab, you'll need to have something being recorded. For that keep your sound source running and then open a recorder and hit record. The recorder should show up in the Recording window. There's a drop down menu next to the small speaker icon. One of the available options should get your recorder going. 

Hope this helps rather than confuse.

---

### Post by Curtis6767 on 2012-05-05
Take a look at this. Don't know if it will work for you but it's worth taking a look at? 

[http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html](http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html)

---

### Post by WarDogLRS on 2012-05-05
[B]OK I cant believe I got the sound working,  So how did I get the Sound card to work.

I have Envy Family SC Drivers  on XP which works fine after I installed  Ubuntu 12 over XP These drivers didn't work on Ubuntu. I found Real Tech  drivers that are compatible with my Card so i installed them over the  top of the Envy restarted the Puter and checked XP for sound it was  there working fine.

I restarted & booted into Ubuntu 12 and the sound was now working  & what a relief and surprise that was. So if your having sound  issues try a Different Driver So Sudo that....hehe[/B]

**Good bye Billy **

---

