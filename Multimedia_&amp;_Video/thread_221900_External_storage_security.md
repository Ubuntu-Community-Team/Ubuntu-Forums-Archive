---
title: "External storage security"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by caryb on 2006-07-24
Hi I have installed dapper on a old p3 for the kids (older teanagers) they prefer this old dunger to there XP machines! but I have 1 anoying feature I installed this box & added them with there own accounts. I have connected a Olympus mrobe mp3 player, it shows up as sda & with my account I can access it perfectly but with there accounts they cant view etc because of permission issues. I logged in as me & used the kde system manager & sudo'd to root but it won't let me change permissions to give the kids access to the unit. Does anyone know how to change the permissions to give them full access to there players.

It is realy gratifying to see my kids adopt Linux but this takes the shine off.


Cary

---

### Post by OpsVentus on 2006-07-24
Check your fstab there should be something about mounting the external drive.
What's in there now?
in Terminal:
#gedit /etc/fstab

If you add the drive there, you can set the permissions.

Cheers,
Bart.

---

### Post by chele on 2006-08-08
Why would you need them to access /etc? Check in Users & Groups and make sure that their accounts belong to the same groups as your account. That should set it up.

---

