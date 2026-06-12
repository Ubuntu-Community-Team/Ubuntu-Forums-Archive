---
title: "How to add device for sound input"
date: 2011-05-02
forum: Multimedia Software
---

### Post by nbafan on 2011-05-02
Hi,
I delete input device. How to fox it? All the sound is working only microphone problem.

Help
[IMG]http://www.clubman.lt/saound.jpg[/IMG]

---

### Post by nbafan on 2011-05-06
any solutions?

---

### Post by lidex on 2011-05-06
Do you have a duplex profile selected on the hardware tab?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

