---
title: "NX Server, policykit, remote privileges"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-11-08
Can ANYONE help, please ?

I have built a new machine, to replace my old 8.10 box. I have put 10.10 on it, configured wireless networks fine, installed my bits and pieces (Vuze, Webmin, Samba, SSH) ready for use as a media server.

I also installed NoMachine (NX) Server, so I can remotely connect in. So far so good - works perfectly.

Now the rub.

When I try to perform certain admin tasks (for example, edit the "eth0" connection, using Network Manager), the button is greyed out. I cannot perform the operation.

This happened with my 8.10 setup. I recall after MUCH googling that it was down to some "policykit" issue. Drawing on my Windows knowledge, I would imagine this is similar to the security profiles you can determine in Terminal Server. Anyway, I installed some GUI tool (gnome-policykit-authorizations) to allow me to edit the relevant attribute, and hey presto !

Now it seems that tool has been removed, and I am helpless. So the question is: can anyone tell me what I need to do, to get NX to be able to adminster the machine fully ? From what I recall, the issue is there is a security setting which prevents remote users acting as administrators.

---

### Post by Jethro_uk on 2010-11-08
Right, I have spent 2 hours googling, and discovered we are looking at this polkit-1 mechanism. I know where the files are stored. However I haven't the faintest idea what I need to do to solve this problem. I really don't know what I need to put in these files, to tell Ubuntu that when I log in via NX, I want to be able to adminster the machine.

---

### Post by Jethro_uk on 2010-11-09
I have spent 4 hours having to google through whispers and rumour, until I managed to fix this issue. Considering the ambitions the linux fraternity hold out for Ubuntu, and linux in general, I cannot believe the documentation and support is so amateurish. I guess you get what you pay for.

I have solved this problem. Probably not "correctly", but after a wasted day, believe me, it's enough.

First things first. Documentation for polkit-1 is pretty sparse. Even worse, it's probably NOT polkit-1's documentation you need anyway. It's whoever supplied the program you are working with.

In my case, it's NetworkManager. After much trawling, I discovered that polkit-1 reads from /usr/share/polkit-1/actions/

in that dir, are XML files, which correspond to the program which is locked down. In my case, it was /usr/share/polkit-1/actions/org.freedesktop.network-manager-settings.system.policy


If you open this file, you will see:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>

  <vendor>NetworkManager</vendor>
  <vendor_url>http://www.gnome.org/projects/NetworkManager</vendor_url>
  <icon_name>nm-icon</icon_name>

  <action id="org.freedesktop.network-manager-settings.system.modify">
    <description>Modify system connections</description>
    <message>System policy prevents modification of system settings</message>
    <defaults>
      <allow_inactive>**no**</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>
```

the secret is the <allow_inactive> element. Change "no" to "yes" (there are a few instances throughout the file. I changed them all). Logout, login, and presto ! the "Edit" button is now active. Now I imagine using one of the "auth_admin" type values would be a better idea. But since I can't find a definitive explanation of what they do, I am leaving it as that. And if some wiseass dares to reply "It's obvious, dimwit", I'll just question the wisdom of playing around with such a sensitive part of the system on intuition.

I apologise for my tone here. I have worked in IT for 25 years, and never once have spent this long on any issue with the Microsoft products I work with for a living. True they are cranky, and not the best at times, but I have never had them simply remove a tool, and then leave users to their own devices.

The reason I am so worked up about this, is that the machine I am configuring needs to be inaccessible, once configured. So not being able to edit network connections when logged in via NX, would have been a show-stopper.

Oh well, have a good night, folks.

---

### Post by Jethro_uk on 2010-11-11
UPDATE:

Watch out if you apply any system updates ... something seems to think it knows better than you, and replaces your modified file with the original. You will need to delete the file and rename the one ending in "~" to remove the "~" or you will be facing greyed out buttons again.

I believe that Microsoft have infiltrated the Ubuntu team, and are wrecking it from the inside.

---

### Post by minmax on 2010-11-15
Great Work Jethro_uk!!
It works for me by editing /usr/share/polkit-1/actions/org.freedesktop.udisks.policy in order to access my ntfs windows partitions as a remote user via nx (linux mint 10).
Thank you for documenting your research =D>

__

---

### Post by Jethro_uk on 2010-11-16
> **minmax said:**
> Great Work Jethro_uk!!
It works for me by editing /usr/share/polkit-1/actions/org.freedesktop.udisks.policy in order to access my ntfs windows partitions as a remote user via nx (linux mint 10).
Thank you for documenting your research =D>

__

Pleased to have put something back :P However, I'd love to know who decides what goes in that directory ... presumably whoever maintains the program in question ?

---

### Post by AlexandreMBM on 2013-02-20
minmax, I need this. How to make?

---

### Post by wildmanne39 on 2013-02-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

