---
title: "Automating /dev/ttySL0 access non user"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by gimmee on 2006-05-04
Hi all

I have setup a slmodemd driver and are acessing the net fine through my winmodem and gnome-ppp or wvdial.

Except when I log on as my normal user i have to goto terminal and
su
cd /dev
ln -s /dev/ttySL0 /dev/modem
chmod 666 ttySL0

This then allows me as non root user to access the modem device and dial in.

How do I add these commands to my startup script so I dont have to do this each time as non root.

I am using the debian script that came with slmodem tarball and tried adding the above commands but to no avail. Very much a beginner at linux so I am probably adding to the script wrong or something.

Look forward to any help you ca give me

Thanks

Gimmee (New Zealand)](*,)

---

### Post by gimmee on 2006-05-14
Hi all

Found my problem. SLModemd daemon sets the ttySL0 with soft link tp pts folder with Group permission set tp uucp.

I added my self to the uucp group and I had permissions to use modem device as user.

Cool.

Laters

Gimmee (I dont want anything thts just my nickname)

---

