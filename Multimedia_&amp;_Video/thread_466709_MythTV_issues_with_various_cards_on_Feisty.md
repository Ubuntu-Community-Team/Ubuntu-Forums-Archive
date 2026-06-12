---
title: "MythTV issues with various cards on Feisty"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by Aleister on 2007-06-07
I have spent the last week attempting to get MythTV to work properly - reading every post, following every guide I can find, and even using three different tv tuners. I am using 7.04.

Cards tried:

Nvidia NVTV - Could not ever get card to recognize, could not get remote to work at all

Leadtek TV2000XP Expert - Could get video, but about 1 frame per second. Remote would work fine when testing with irw, but would not work with MythTV (tried various config files, etc..)

MSI TV@nywhere - Card would detect but video was extremely laggy. Remote would not work.

The system has an Athlon XP 2500+, 1GB ram, 320GB HD, 9600Pro video (s-video out works fine), on-board sound. It is a very fresh install of 7.04.

This whole ordeal has been a nightmare to say the least. Every guide I find has a completely different method of getting everything working, so one would think that I could eventually find one that would work for me ;)

If anyone with any of these cards on 7.04 has any tips, I would love to hear them.

Otherwise, can anyone recommend a tuner (with a remote of course) that will actually work nicely with default installs of mythtv and lirc? Thanks for any info :)

---

### Post by rhpot1991 on 2007-06-07
If you are looking for standard definition go with a Hauppauge card.  The PVR-150 works out of the box, the remote is easy to configure, and they can be had from Circuit City for around $70 if you have them price match their website.

Here is a list of known working cards:
[http://www.mythtv.org/wiki/index.php/Category:Video_capture_cards](http://www.mythtv.org/wiki/index.php/Category:Video_capture_cards)

Good luck with the 9600 pro, svideo works fine while not in mythtv.  But, the moment you try to display actual video in mythtv you will notice that you only see the top 1/3rd or so of the screen.  The way to fix this requires you to have your cpu do a ton of work and to apply a hack to mythtv in order to fix a color problem that comes about from displaying video different.  My solution was to just buy a new nvidia card.

---

### Post by Aleister on 2007-06-08
**rhpot1991**: Thanks for the suggestion - I will pick one up and give it a shot :)

As far as the 9600, it seems to be doing ok actually. I never had any problems with the MythTV interface showing up through s-video, and tv looked ok too, although for testing purposes I was just using the s-video input on my computer's LCD - once I have everything working I will be using a standard crt tv for this setup.

As a side note - I noticed that some of the remotes I tested seemed to perform various operations in ubuntu/gnome itself (without mythtv running). For example, the volume buttons would bring up a volume adjustment bar.

While I did not see any info on this, would you happen to know if this is something that can interfere with the remotes operation within mythtv? If so, I am sure there is a way to disable it - I will look for info on that.

---

### Post by tgm4883 on 2007-06-08
The PVR-150 is a good card, make sure you either get one with a remote.  Or if you don't, get something like the Media Center remote (I prefer the media center remote.  It is an excellent piece of hardware)

You didn't specify which guide you were using, so I really hope it was this one as it is an excellent guide.
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by Aleister on 2007-06-08
**tgm4883**: That actually is the guide I ended up sticking with - it is nicely done.

Well, I just came back from CC with a PVR-150, so I will hope for the best :) It did come with a remote. I made sure it was not one of the 1600 series that some say they have been getting when they buy a PVR-150 (mentioned in the MythTV wiki entry).

I will post back with results :)

---

### Post by rhpot1991 on 2007-06-08
As far as the remote go I have only ever messed with ones that are used by the Hauppauge cards, and with lirc.  Doing it this way you need to have a config which tells ivtv exactly what that remote keystroke does in each program.

Lirc howto is straightforward and easy to follow:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

With my prv-350 I used the stock remote, and with the pvr-150 I used an all-for-one universal remote.

---

### Post by Aleister on 2007-06-08
**Update:** 

I reconfigured MythTV to use the new card, and it appears to have recognized it with no problems (I have not connected it to cable yet though).

I then reconfigured lirc (using the proper hardware.conf and lircd.conf files), and when I test with irw, it works great - it shows the proper text for every button!

The only thing left is getting the remote to work in MythTV. I have what I believe to be the proper lircrc files in these locations (including symbolic links)

/home/(mainuser)/.lircrc
/home/(mainuser)/.mythtv/lircrc
/home/mythtv/.lircrc
/home/mythtv/.mythtv/lircrc

(for the record though, I am just running MythTV as my main user)

Absolutely no signs of life from the remote in MythTV, but I am probably just missing something small and will keep trying things out :)

---

### Post by Aleister on 2007-06-08
**Solved!** I had to chown /dev/lircd and /dev/lirc0 to my main user account - it ended up just being a permission problem. The remote now works perfectly in MythTV! Now I just need to test it with the cable connected ;)

---

