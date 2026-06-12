---
title: "Can I teach Mythbuntu the power code for my TV or Stereo?"
date: 2008-05-01
forum: Mythbuntu
---

### Post by freymann on 2008-05-01
I was wondering if there were programs included in MythBuntu (I'm using 7.10 at the moment) that would learn the power code for my TV and Stereo? To which I'd then like to reprogram some non-used buttons on my MCE Remote (that is working great right now) to be able to turn on/off the TV or Stereo.

My MCE remote/blaster is currently doing a fine job of controlling MythTV and changing channels on our external satellite receiver (so the blasting part is working).

---

### Post by tgm4883 on 2008-05-01
You would either have to use ir blasting to power the tv/stereo on/off or have a programable remote (which some of the MCEUSB2 remotes are programmable for TV Power and Volume)

---

### Post by freymann on 2008-05-01
> **tgm4883 said:**
> You would either have to use ir blasting to power the tv/stereo on/off or have a programable remote (which some of the MCEUSB2 remotes are programmable for TV Power and Volume)

 Yes, that is what I'm after in the long run.

 I have 3 setups. The one in the basement had the silver remote that I was able to teach the power button to the TV on.

 But the other two stations... those remotes aren't teachable (as far as I know?) so is there software included with MythBuntu that will record the signal when I press the Power Button on the TV remote? with the hopes of putting that into the lircd.conf file and attaching it to a non-used button.

 Same question as my first post..

---

### Post by grytpype on 2008-05-01
> **freymann said:**
> My MCE remote/blaster is currently doing a fine job of controlling MythTV and changing channels on our external satellite receiver (so the blasting part is working).

On the MCE remote, you can train certain buttons to emit any signal you want.  You can train (IIRC) TV Power, PC Power, Vol+ and Vol-.  

If I understand you, you want to turn your TV on and off with the MCE remote. You can just train the remote to do that, you don't need to go through the MythTv box and then the blaster.

---

### Post by freymann on 2008-05-01
> **grytpype said:**
> On the MCE remote, you can train certain buttons to emit any signal you want.  You can train (IIRC) TV Power, PC Power, Vol+ and Vol-.  

If I understand you, you want to turn your TV on and off with the MCE remote. You can just train the remote to do that, you don't need to go through the MythTv box and then the blaster.

 That is correct.

 I have 3 different versions of the remote.

 I have this one:

[http://eirikso.com/2005/11/16/how-to-program-the-buttons-on-your-mce-remote/]("http://eirikso.com/2005/11/16/how-to-program-the-buttons-on-your-mce-remote/")

 and was able to teach it how to flip my tv on/off.

 My other two remotes are different. Once is black [and has the 4 colored button across the bottom], the other is silver. Can I program the TV power button on those remotes too?

---

### Post by tgm4883 on 2008-05-02
Take a look at this page

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

---

### Post by grytpype on 2008-05-02
> **freymann said:**
> 

 My other two remotes are different. Once is black [and has the 4 colored button across the bottom], the other is silver. Can I program the TV power button on those remotes too?

Check out this page;

[http://www.mythtv.org/wiki/index.php/MCE_Remote#Configuring_the_Buttons](http://www.mythtv.org/wiki/index.php/MCE_Remote#Configuring_the_Buttons)

I think all versions of the MCE remote have programmable buttons.

---

### Post by tgm4883 on 2008-05-02
> **grytpype said:**
> Check out this page;

[http://www.mythtv.org/wiki/index.php/MCE_Remote#Configuring_the_Buttons](http://www.mythtv.org/wiki/index.php/MCE_Remote#Configuring_the_Buttons)

I think all versions of the MCE remote have programmable buttons.

Do look at that page.  But FYI, not all MCE remotes have programmable buttons.  (I have one that doesn't.  It is collecting dust now)

---

### Post by freymann on 2008-05-02
> **tgm4883 said:**
> Take a look at this page

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

Thanks.

When I use irrecord it just times out and stops. It doesn't see or record any keypresses from the TV Remote.

I ran into this before with another MCE system I tried before MythBuntu and was told to go buy some USB-UIRTS and my problems would go away. Since I have 3 PVR-150's with remotes and the ir transceivers I figured I'd stick with them.

It's not a show stopper if we have to flip on the Tv and Stereo manually as we walk by before sitting down and using the Myth remote.

Maybe I'll try again after I eventually update to 8.04.

---

