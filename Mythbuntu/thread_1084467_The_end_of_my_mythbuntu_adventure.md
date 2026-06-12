---
title: "The end of my mythbuntu adventure"
date: 2009-03-02
forum: Mythbuntu
---

### Post by GuiGuy on 2009-03-02
I have just passed the first anniversary with mythbuntu driving our home entertainment center. Generally, it's been a good experience. 

Yesterday on switch on the sound stopped working. 

Nothing has changed on the system. Settings are fine, as I had diligently written them down. Hardware is OK (sound works when I run from a livecd desktop). I have exhausted the[ troubleshooting guide]("https://wiki.ubuntu.com/DebuggingSoundProblems") and the links it leads to. I have worn google out, if that's possible. I have probably spent more than 12 hours now trying every suggestion that's out there short of doing a re-install. Everything seems futile and in any case, I am probably starting to make too many mistakes now. 

At this point I've had to fall back to the set-top box and really don't think I have the energy to continue. 

As what may well be a parting observation, it does seem to me that one of the most frustrating aspect of linux has been getting sound restarted when it stops. 

Thanks for listening, but I don't really feel much better.

---

### Post by enchesss on 2009-03-02
keep trying - may the force be with you

---

### Post by prshah on 2009-03-02
> **GuiGuy said:**
> 
Yesterday on switch on the sound stopped working. 


If you are using Intel onboard audio, I too lose the sound hardware entirely with some kernel updates.

Currently, I use a previous kernel choice from the GRUB boot menu.

Maybe this will help you?

---

### Post by Caps18 on 2009-03-02
I switched to Xine (search here for command line to use).  The built in player doesn't use the right soundcard for some reason.

You can also pick different sound outputs and try that.  You may need to restart after each change.  It usually is on default, but I'm using DSP2 now.  I'm not sure why it switched.

What do your frontend logs say?

---

### Post by GuiGuy on 2009-03-02
> **Caps18 said:**
> 
What do your frontend logs say?

I don't know, but I did find the problem:

I usually use alsamixer to check the sound settings. It was telling me all was well. 

I had done the usual checks (aplay -l, amixer etc). They also told me everything should be working 

While getting ready to throw the damn lot into the trash last night, I accidentally (or coincidentally) started gnome mixer. It's telling me the master channel is muted!!?? :confused: 

I unchecked the mute button and away it went. 

Linux- frustrating one day, infuriating the next. 

Thanks

---

### Post by Caps18 on 2009-03-02
The simple fix but hidden away choice strikes again.

This is why I still use 7.10.  Everything is just right and works.  As long as I don't change anything, it stays happy.

(It's also kind of cool that you got advice from all around the world.)

---

### Post by klc5555 on 2009-03-02
> **Caps18 said:**
> The simple fix but hidden away choice strikes again.

This is why I still use 7.10.  Everything is just right and works.  As long as I don't change anything, it stays happy.


This seems to be the main problem with the "a new version every six months without fail" philosophy. About the time a given OS version has just begun to become really stable and really reliable, it's two versions behind and about to hit the End of Service wall. Non-security patches and good backport support dry up before that.

---

### Post by keimol on 2009-03-02
Lately my machine seems to boot up with the master channel muted too. It used to remember the previous settings, but now it comes up muted.

Edit: I have onboard Intel audio, aplay identifies it as an ALC888.

---

### Post by Cyclone42 on 2009-03-02
Sound/audio is bar far Linux's Achilles-heal. Linux users like to pick on Windows a lot, but Windows just plain works.  I have never had audio problems with a Windows machine.  Linux developers know that audio is a problem with Linux, and they just keep piling layer upon layer upon layer of software, to try to fix the problems, and it doesn't work (first ALSA, then JACK, then pulse-audio, next heaven knows what...)

Sorry, this is a sore spot for me, too.

---

### Post by superm1 on 2009-03-02
> **keimol said:**
> Lately my machine seems to boot up with the master channel muted too. It used to remember the previous settings, but now it comes up muted.

Edit: I have onboard Intel audio, aplay identifies it as an ALC888.

Try doing this after setting your settings:
```

sudo /etc/init.d/alsa-utils stop
sudo reboot

```
If it still doesn't come up right then:
```

sudo /etc/init.d/alsa-utils reset
sudo reboot

```
<set your settings>
```

sudo /etc/init.d/alsa-utils stop
sudo reboot
```

---

### Post by keimol on 2009-03-03
Thanks superm1, but I'm well aware that alsa-utils should save the sound state to /var/lib/alsa/asound.state (IIRC) :)

Normally I've set my settings and reboot to see that they're working and say "chattr +i" to that file (hibernation experiments used to lead to situations where an "impossible state" got saved into asound.state and no amount of fiddling with alsamixer would bring sound back). And no, the file is not immutable right now (since I'm not doing hibernation anymore).

---

### Post by GuiGuy on 2009-03-04
> **GuiGuy said:**
> 
Yesterday on switch on the sound stopped working. 


First, thanks for all the replies. 

Second, here's a tip for those not comfortable working out of a shell and having problems with sound when everything tells you it should be working;

I've now had problems with two machines, one mythbuntu, the other kubuntu. 

I was exhausted. Nothing would coax it. 

As a last resort, I thought I'd try another mixer. I installed the gnome alsa mixer. It's in the repository. It showed properties that I wasn't aware of. 

As mentioned, in the case of the mythbuntu machine it highlighted the master control as muted, when everything else said it was on!!??

On the kubuntu machine the line jack sensor had been set to off. Again, only the gnome mixer showed that property.

If you're stuck, try the gnome alsa mixer. At least it seems to visualize EVERYTHING that's going on. It worked for me. 

Thanks

PS: Is there a [SOLVED] marker for these threads?

---

### Post by GuiGuy on 2009-03-04
> **Cyclone42 said:**
> Sound/audio is bar far Linux's Achilles-heal. Linux users like to pick on Windows a lot, but Windows just plain works.  I have never had audio problems with a Windows machine.

Agreed. It's something that urgently needs sorting.

BTW, why don't any of the GUI mixer panels have a TEST button?

---

### Post by klc5555 on 2009-03-05
> **keimol said:**
> Thanks superm1, but I'm well aware that alsa-utils should save the sound state to /var/lib/alsa/asound.state (IIRC) :)

Normally I've set my settings and reboot to see that they're working and say "chattr +i" to that file (hibernation experiments used to lead to situations where an "impossible state" got saved into asound.state and no amount of fiddling with alsamixer would bring sound back). And no, the file is not immutable right now (since I'm not doing hibernation anymore).

I suppose you could always use the nuclear option for wonky asound.state files: if you ever get a set of really good mixer settings and have them saved to /etc/asound.state, you could make a second copy of the file as /etc/asound.state.ref  Then write a one-line bootup script to add to the init.d sequence (or just run it sudo as necessary):

cp /etc/asound.state.ref  /etc/asound.state

---

