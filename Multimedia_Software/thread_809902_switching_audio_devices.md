---
title: "switching audio devices"
date: 2008-05-27
forum: Multimedia Software
---

### Post by akahige on 2008-05-27
I'm trying to get Skype running on my Hardy system. Installed just fine.

What I'm having a problem with is figuring out how to switch the audio device from the speakers to my USB headphones.

I looked through the Sound Preferences, but couldn't make any sense of what I was seeing. I see the headphones under "Default Mixer Tracks", and when I do this:

```
asoundconf list
```

...I get this:

```
Names of available sound cards:
NVidia
Headset
```


I'm wondering if it might have something to do with the USB config for VMware (it's set so that nothing automounts to keep Gnome from continually stealing the external drives), but if the sound commands are seeing headphones, then I don't know what's going on.

Any thoughts...?

---

### Post by ramachandren on 2008-05-27
You can set your Headset as the default device using the following command.

```
asoundconf set-default-card Headset
```

---

### Post by akahige on 2008-05-27
Yes, but how do I switch it back? Isn't there a way to change back and forth from the GUI?

---

### Post by akahige on 2008-05-27
I hate replying to myself, but...

I tried the asoundconf Headset switch. Didn't actually *do* anything. So, I'm back to square one...

Anybody know how to get the headphones to show up?

---

