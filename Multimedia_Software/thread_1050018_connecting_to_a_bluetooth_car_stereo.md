---
title: "connecting to a bluetooth car stereo"
date: 2009-01-25
forum: Multimedia Software
---

### Post by bluescreen303 on 2009-01-25
Hi,

I'm trying to get my music player to play to my car stereo, using bluetooth.
The stereo acts like a headset, at least that's what my phone tells me (my phone is successfully paired with the stereo).
Now, I did already connect successfully to a headset at home, so I already know how to configure alsa and stuff.

The problem is this:
The car stereo is not detectable when doing a scan, and it does not have a 'pairing mode'. The way it worked with my mobile phone is like this:
When I press the bluetooth button on the car stereo, it looks around for devices itself and tries to pair. For example, if I remove the car stereo from my bluetooth devices on my phone, and press the button, I don't have to scan for it or anything, it just connects to my phone and asks to pair.

So I guess I need to setup my laptop to be discoverable and act as a mobile phone (what service would the car stereo be looking for?), to get this reverse-pairing working.

Has anyone got some experience with this?
Do I need to run some kind of daemon to get this working? Is this just during the setup (to get the mac address of the car stero) or will I need to stay running/configuring a bit different?

Thanks for any help,
Mathijs

---

