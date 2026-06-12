---
title: "Pulseaudio with OSS backend"
date: 2012-09-08
forum: Multimedia Software
---

### Post by Major_Kong on 2012-09-08
I'm trying to make PulseAudio use OSS instead of Alsa. And, although, I have sucessfully installed OSSv4, pulseaudio seems unable to use it.

OSSv4 Installation Procedure:

[LIST]
[*]Download the deb package from [http://www.opensound.com/](http://www.opensound.com/) . The OSSv4 packages in the repositories are currently broken.
[*]run 'sudo dpkg-reconfigure linux-sound-base' and choose OSS.
[*]reboot
[*]run 'sudo dpkg -i oss-linux-4.2-2007_amd64.deb'
[/LIST]

After this, OSSv4 was working perfectly - tested it in applications that i had setup to use it directly. So all that remained was configuring PulseAudio.
After reading the available guides - [http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html), etc. - I edited the pulseaudio configuration file, but the oss module doesn't seem to be working. By loading the module directly from the pulseaudio CLI i get a message that the module has been deprecated. Is PulseAudio support for OSS currently broken ?

Thank You,
MK

---

### Post by Major_Kong on 2012-10-06
Any thoughts ?

---

### Post by Major_Kong on 2012-10-06
Making a few questions in the pulseaudio IRC channel, it seems it never supported OSSv4. :(

---

