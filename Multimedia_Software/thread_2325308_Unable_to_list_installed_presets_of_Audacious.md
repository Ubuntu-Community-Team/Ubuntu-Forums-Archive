---
title: "Unable to list installed presets of Audacious"
date: 2016-05-21
forum: Multimedia Software
---

### Post by aashish2 on 2016-05-21
Hi All,
I installed Audacious player V3.2.1 in Ubuntu 12.04LTS. I am trying to install equaliser presets but they never get listed under Presets->Load Preset-><An emptly list>.
Here's what I did:

1. Download the Winamp preset EQ's
2. Open up terminal
3. wget [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz)
4. To install the presets for the Audacious media player type:
   gunzip -c winamp_presets.gz > ~/.config/audacious/eq.preset
5. Close Audacious and start it again.

These steps have worked for almost anyone who has had a problem importing presets, but it didn't work for me. The presets list is still empty as before. 
This is VERY aggravating. ](*,) Requesting for help!

If any other details are needed, kindly let me know.
Thanks,
Aashish.

---

### Post by howefield on 2016-05-21
Doesn't appear to be a valid url, are you following a tutorial ?

---

### Post by aashish2 on 2016-05-21
I may have obtained the presets file from another URL. This link works: [http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz](http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz) .
But everywhere I looked for solving this issue, the steps remain the same: download the presets file and copy it to ~/.config/audacious/eq.preset. 
I just can't figure why audacious fails to see the presets. I'll upload my presets file here for reference (winamp_presets.gz).

---

### Post by aashish2 on 2016-05-21
I found another thread reporting the same problem.
[http://ubuntuforums.org/showthread.php?t=1609390](http://ubuntuforums.org/showthread.php?t=1609390)
 But the OP solved it by creating his own eq.preset file and copying it to ~/.config/audacious/. I downloaded the same file too but that didn't work either.

---

### Post by mc4man on 2016-05-21
see here - [http://ubuntuforums.org/showthread.php?t=2309352&p=13421915&viewfull=1#post13421915](http://ubuntuforums.org/showthread.php?t=2309352&p=13421915&viewfull=1#post13421915)
works fine, screen

---

### Post by aashish2 on 2016-05-23
I tried the exact same thing, but the presets list is still empty.
Anything else I could try?

---

### Post by howefield on 2016-05-23
> **aashish2 said:**
> I tried the exact same thing, but the presets list is still empty.
Anything else I could try?

The above posted by mc4man works perfectly but you might try changing to the classic skin.

---

### Post by aashish2 on 2016-05-23
I changed the skin to classic, and then to default. Still no luck. This could have something to do with audacious version I have (3.2.1) or updating some other necessary libs/packages. However, I can't risk updating my system due to other reasons (environment setup for building certain libs.

I think I'll just manually set the equalizer for now. 

Thanks for the prompt responses, though. I appreciate it.

Regards,
Aashish

---

### Post by pete55 on 2016-07-04
Open Terminal and paste:

rm $HOME/.config/audacious/eq.preset
cat > $HOME/.config/audacious/eq.preset << EOF
[Presets]
Preset0=Classical
Preset1=Club
Preset2=Dance
Preset3=Flat
Preset4=Live
Preset5=Laptop Speakers/Headphone
Preset6=Rock
Preset7=Pop
Preset8=Full Bass and Treble
Preset9=Full Bass
Preset10=Full Treble
Preset11=Soft
Preset12=Party
Preset13=Ska
Preset14=Soft Rock
Preset15=Large Hall
Preset16=Reggae
Preset17=Techno
[Classical]
Preamp=0.375
Band0=0.375
Band1=0.375
Band2=0.375
Band3=0.375
Band4=0.375
Band5=0.375
Band6=-4.5
Band7=-4.5
Band8=-4.5
Band9=-6
[Club]
Preamp=0.375
Band0=0.375
Band1=0.375
Band2=2.25
Band3=3.75
Band4=3.75
Band5=3.75
Band6=2.25
Band7=0.375
Band8=0.375
Band9=0.375
[Dance]
Preamp=0.375
Band0=6
Band1=4.5
Band2=1.5
Band3=0
Band4=0
Band5=-3.75
Band6=-4.5
Band7=-4.5
Band8=0
Band9=0
[Flat]
Preamp=0.375
Band0=0.375
Band1=0.375
Band2=0.375
Band3=0.375
Band4=0.375
Band5=0.375
Band6=0.375
Band7=0.375
Band8=0.375
Band9=0.375
[Live]
Preamp=0.375
Band0=-3
Band1=0.375
Band2=2.625
Band3=3.375
Band4=3.75
Band5=3.75
Band6=2.625
Band7=1.875
Band8=1.875
Band9=1.5
[Laptop Speakers/Headphone]
Preamp=0.375
Band0=3
Band1=6.75
Band2=3.375
Band3=-2.25
Band4=-1.5
Band5=1.125
Band6=3
Band7=6
Band8=7.875
Band9=9
[Rock]
Preamp=0.375
Band0=4.875
Band1=3
Band2=-3.375
Band3=-4.875
Band4=-2.25
Band5=2.625
Band6=5.625
Band7=6.75
Band8=6.75
Band9=6.75
[Pop]
Preamp=0.375
Band0=-1.125
Band1=3
Band2=4.5
Band3=4.875
Band4=3.375
Band5=-0.75
Band6=-1.5
Band7=-1.5
Band8=-1.125
Band9=-1.125
[Full Bass and Treble]
Preamp=0.375
Band0=4.5
Band1=3.75
Band2=0.375
Band3=-4.5
Band4=-3
Band5=1.125
Band6=5.25
Band7=6.75
Band8=7.5
Band9=7.5
[Full Bass]
Preamp=0.375
Band0=6
Band1=6
Band2=6
Band3=3.75
Band4=1.125
Band5=-2.625
Band6=-5.25
Band7=-6.375
Band8=-6.75
Band9=-6.75
[Full Treble]
Preamp=0.375
Band0=-6
Band1=-6
Band2=-6
Band3=-2.625
Band4=1.875
Band5=6.75
Band6=9.75
Band7=9.75
Band8=9.75
Band9=10.5
[Soft]
Preamp=0.375
Band0=3
Band1=1.125
Band2=-0.75
Band3=-1.5
Band4=-0.75
Band5=2.625
Band6=5.25
Band7=6
Band8=6.75
Band9=7.5
[Party]
Preamp=0.375
Band0=4.5
Band1=4.5
Band2=0.375
Band3=0.375
Band4=0.375
Band5=0.375
Band6=0.375
Band7=0.375
Band8=4.5
Band9=4.5
[Ska]
Preamp=0.375
Band0=-1.5
Band1=-3
Band2=-2.625
Band3=-0.375
Band4=2.625
Band5=3.75
Band6=5.625
Band7=6
Band8=6.75
Band9=6
[Soft Rock]
Preamp=0.375
Band0=2.625
Band1=2.625
Band2=1.5
Band3=-0.375
Band4=-2.625
Band5=-3.375
Band6=-2.25
Band7=-0.375
Band8=1.875
Band9=5.625
[Large Hall]
Preamp=0.375
Band0=6.375
Band1=6.375
Band2=3.75
Band3=3.75
Band4=0.375
Band5=-3
Band6=-3
Band7=-3
Band8=0.375
Band9=0.375
[Reggae]
Preamp=0.375
Band0=0.375
Band1=0.375
Band2=-0.375
Band3=-3.75
Band4=0.375
Band5=4.125
Band6=4.125
Band7=0.375
Band8=0.375
Band9=0.375
[Techno]
Preamp=0.375
Band0=4.875
Band1=3.75
Band2=0.375
Band3=-3.375
Band4=-3
Band5=0.375
Band6=4.875
Band7=6
Band8=6
Band9=5.625
EOF

---

