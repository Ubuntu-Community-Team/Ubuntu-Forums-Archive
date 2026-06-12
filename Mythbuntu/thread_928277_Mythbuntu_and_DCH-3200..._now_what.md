---
title: "Mythbuntu and DCH-3200... now what?"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Anastomosis on 2008-09-23
Hi, I thought I almost had this thing set up, with all the help available on the net. Unfortunately, it seems I'm missing one final step.

I have a Motorola DCH-3200 and it is connected to my PC via Firewire. I installed Mythbuntu and it appears to be working fine, as far as the music/videos/DVDs go.

The firewire connection appears to be working. The firewire_tester app works great, as long as I have it on a non-encrypted channel, as well as the plugctl program. 

Also, I compiled the 6200ch from source, and I can use this to change the channel from a terminal window just great. 

I signed up on schedulesdirect, and in MythSetup, it downloaded all the channels no problem. I set it to a non-encrypted channel to start (5 in my case), assigned the channel changing program to the location of my 6200ch binary, and then ran the frontend. 

Unfortunately, when I press "Watch TV" in the frontend, it goes to a blank screen and then right back to the menu. There definitely is a channel 5, as I can watch it if I just connect the cable box to the TV, but it just is not working. 

Any suggestions? Did I forget some crucial step?

---

### Post by mrand on 2008-09-24
> **Anastomosis said:**
> Hi, I thought I almost had this thing set up, with all the help available on the net. Unfortunately, it seems I'm missing one final step.

I have a Motorola DCH-3200 and it is connected to my PC via Firewire. I installed Mythbuntu and it appears to be working fine, as far as the music/videos/DVDs go.

The firewire connection appears to be working. The firewire_tester app works great, as long as I have it on a non-encrypted channel, as well as the plugctl program. 

Also, I compiled the 6200ch from source, and I can use this to change the channel from a terminal window just great. 

I signed up on schedulesdirect, and in MythSetup, it downloaded all the channels no problem. I set it to a non-encrypted channel to start (5 in my case), assigned the channel changing program to the location of my 6200ch binary, and then ran the frontend. 

Unfortunately, when I press "Watch TV" in the frontend, it goes to a blank screen and then right back to the menu. There definitely is a channel 5, as I can watch it if I just connect the cable box to the TV, but it just is not working. 

Any suggestions? Did I forget some crucial step?Howdy,

The first step in diagnosing most video problems is to divide the problem in half: does the video work without MythTV?  I don't have firewire video so I don't know the answer for sure, but I would be very surprised if there weren't way to view video from firewire external to Myth.  I suggest searching the forums, MythTV mailing list, and/or mythtv wiki for how to do that and verify that you are able to view the stream.  Once you know that works, then go through the config on Myth with a fine tooth comb.

[INDENT]   Marc[/INDENT]

---

### Post by majoridiot on 2008-09-26
> **Anastomosis said:**
> Hi, I thought I almost had this thing set up, with all the help available on the net. Unfortunately, it seems I'm missing one final step.

I have a Motorola DCH-3200 and it is connected to my PC via Firewire. I installed Mythbuntu and it appears to be working fine, as far as the music/videos/DVDs go.

The firewire connection appears to be working. The firewire_tester app works great, as long as I have it on a non-encrypted channel, as well as the plugctl program. 

Also, I compiled the 6200ch from source, and I can use this to change the channel from a terminal window just great. 

I signed up on schedulesdirect, and in MythSetup, it downloaded all the channels no problem. I set it to a non-encrypted channel to start (5 in my case), assigned the channel changing program to the location of my 6200ch binary, and then ran the frontend. 

Unfortunately, when I press "Watch TV" in the frontend, it goes to a blank screen and then right back to the menu. There definitely is a channel 5, as I can watch it if I just connect the cable box to the TV, but it just is not working. 

Any suggestions? Did I forget some crucial step?

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

---

