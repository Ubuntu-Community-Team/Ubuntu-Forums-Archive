---
title: "mod can use pulse, but other users cannot"
date: 2009-07-08
forum: Multimedia Software
---

### Post by markp1989 on 2009-07-08
I just installed puleaudio and mpd on my command line install + openbox using these guides:

[https://help.ubuntu.com/community/MPD](https://help.ubuntu.com/community/MPD)
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

mpd works, and i can use pulse audio if i run moovida as root, but i dont want to do that, if i run moovida as a regular user, then i get no sound now pulse has been installed? 

im assuming this is a permission problem, how do i fix this?

Thanks Markp1989

---

### Post by cariboo on 2009-07-08
Is your regular user a member of the audio group? If not go to System-->Administration-->Users & Groups and add the group to the user.

---

### Post by markbuntu on 2009-07-08
For now, you need to be a member of these groups

pulse
pulse-access
pulse-rt

Though this is being deprecated in version 0.9.16.

---

