---
title: "One user has sound, another doesn't"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by phstpok on 2007-07-10
I had a couple of strange things happen today. First, I entered a sudo command and got an error message thatI'm not in the sudoers file and would be reported. I checked and the /etc/sudoers had no changes since I installed Ubuntu 6.10, upgrading to 7.04 when it was released. I couldn't read the file, no permissions, and I couldn't su, accepting neither user nor root password. 

I also noticed my sound icon in the notification area had the mute x showing. Tried opening volume control and got error "No volume control gstreamers plugins and/or devices found". Tried xmms, mplayer etc. but no sound. aplay -l returns error 221, no sound card found, yet as the second user it finds the card as Ensoniq ed1371.

I logged out and back in as another user which let me sudo visudo to fix that problem. I also found that the sound worked perfectly with this username.

As the first user, I tried through Synaptic re-installing all gstreamer plugins I could find, but to no avail. I'm at a dead loss here. I don't really want to change user, as I have spent a lot of time setting up the first user with loads of aliases, scripts etc.

---

### Post by mitch.c on 2007-07-12
It sounds to me like the first user account is not a member of the appropriate groups. For you problems usiing sudo try:
```
$ cat /etc/group | grep admin
```
If the user is not listed, that's *at least* part of the problem. You shouldn't have needed to make any changes to /etc/sudoers.

For sound, try:
```
$ cat /etc/group | grep audio
```
You need to be a member of this group for sound to work.

---

