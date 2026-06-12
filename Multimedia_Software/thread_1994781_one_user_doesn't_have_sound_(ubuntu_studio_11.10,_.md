---
title: "one user doesn't have sound (ubuntu studio 11.10, xfce)"
date: 2012-06-03
forum: Multimedia Software
---

### Post by dandellion on 2012-06-03
I did a fresh dualboot install of Win7 (bloody job) and Ubuntu Studio 11.10. There was an old Sound Blaster Live! sound card in the box. Sound was nice in Ubuntu but Win7 doesn't have drivers for the card so I took it out leaving integrated one. 
lspci sees it ans says:
> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: ATI Technologies Inc Barts HDMI Audio [Radeon HD 6800 Series]

Now Win plays sound but Ubuntu is silent. 
To check things out, I made a new account and it plays sound both in Enlihtement and in XFCE. My regular account is still silent in both DM's. 

So, cables are OK, speakers work, card is recognized and modules loaded.
In alsamixer everything is pushed up and unmuted. 
xfce-mixer on the panel says it is working with HDA ATI SB (Alsa mixer) and in it is everything pushed up and unmuted. 

Where and what should I tell xfce so I get sound here?

Thanks

---

### Post by dandellion on 2012-06-05
I still have no finar solution for this, but while digging I came to idea that it's the PulseAudio that messes things up. So I uninstalled it 
```
sudo apt-get autoremove pulseaudio
```

I'm not sure if I'll need PulseAudio in the near (or farther) future, but at the present I want some music :)

Would be nice if somebody knows how to fix PA.

---

### Post by brainwash on 2012-06-05
Deleting the user specific configuration/cache folder might help to fix problems with PulseAudio:
```
rm -r ~/.pulse
```

---

