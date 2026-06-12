---
title: "No Sound in Ubuntu 8.10 64bit - complete noob"
date: 2008-12-25
forum: Multimedia Software
---

### Post by CrazyMike on 2008-12-25
Hello all!  I've been browsing as an unregisterd lurker but I finally need to ask some questions.

I'm very very new to Ubuntu and am having a pretty difficult time getting started.  I wanted to give it a shot after several folks have told me how great it is over Windows.  After trying to do this stuff on my own for over a month, I have had more troubles than I expected.

My biggest issue right now is setting up my audio.  I downloaded the updated driver from intel for my mb and did my best to follow the installation instructions but found out I don't have 'permission' do the 'make install' command. 

Then I found the following thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 

but alas, still no audio. (Result 'c' in the troubleshooting above)

Can someone point me in the right direction?  Please use small words - I barely speak linux!

Cheers,

Mike

I've tried some numerous searches however I'm out of patience...

---

### Post by wolfen69 on 2008-12-25
did you do ```
sudo make install
```
sudo is needed for this. not just "make install".

---

### Post by CrazyMike on 2008-12-25
That helped some but a few more hitches:
apparently I have no alsaconf program on this version of ubuntu
cannot find any file called /etc/modules.conf or conf.modules so I can't edit them.  

I don't want to trash linux, but is everything this complicated?

EDIT - sorry I don't want to start out as a whiner.  Just frustrated as I think I've spent over 10 hours on this problem (and a number of others) and they seem to compound.  I'd like to see a smooth running system soon :)

---

### Post by RedSingularity on 2008-12-25
Are you using an Analog or USB setup with your speakers/Headset?

---

### Post by CrazyMike on 2008-12-25
No - I'm only using the coaxial digital output.

---

### Post by RedSingularity on 2008-12-25
Did you try messing in System> Preferences> Sound?

---

### Post by CrazyMike on 2008-12-25
> **Shadow121 said:**
> Did you try messing in System> Preferences> Sound?

Yes, every option.  None gave me an audible test tone...

---

### Post by CrazyMike on 2008-12-28
So is there anything else I could/should do to get the sound to work in Ubuntu???

---

### Post by duanedesign on 2009-01-02
Acouple quick quotes from here might help [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

**Quote:**
Note 1. Intrepid users: due to a bug in the ALSA libraries, your PCM mixer may occasionally become muted or reset to 0% volume. If you cannot hear sound - or hear a faint crackling - refer to Part C, Step 3.

**Quote:**
3. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a bug in Intrepid):

Code:

$ alsamixer -[COLOR="Navy"]Dhw[/COLOR]

[COLOR="Navy"]Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer[/COLOR]

additionally you might try:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)


good luck

---

