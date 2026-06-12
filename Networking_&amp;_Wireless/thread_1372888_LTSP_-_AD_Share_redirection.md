---
title: "LTSP - AD Share redirection"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by greenwaysch on 2010-01-05
I have followed the direction on [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP) to allow our thin client system to connect to our domain, from there I also followed the instructions for redirecting the home folder to the user AD Documents folder. We are using Ubuntu 9.10.
 
When a user logs in using AD credentials no redirection takes place and I'm stuck on where to look next.
 
Our pam_mount.conf.xml looks like this -
 
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
See pam_mount.conf(5) for a description.
-->
<pam_mount>
 
<!-- Volume definitions -->
 
<!-- pam_mount parameters: General tunables -->
<debug enable="0" />
<!--
<luserconf name=".pam_mount.conf.xml" />
-->
<!-- Note that commenting out mntoptions will give you the defaults.
You will need to explicitly initialize it with the empty string
to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="nosuid,nodev" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>
<logout wait="0" hup="0" term="0" kill="0" />
 
<!-- pam_mount parameters: Volume-related -->
<mkmountpoint enable="1" remove="true" />
 
**<volume sgrp="GREENWAYSCHOOL\children" options="username=%(USER),user=%(USER),domain=GREENWAYSCHOOL" fstype="cifs" server="192.168.0.1" path="Children-Documents" mountpoint="/home/GREENWAYSCHOOL/%(DOMAIN_USER)/Documents" />**
 
</pam_mount>
 
Am I correct in thinking that the option "sgrp=" refers to the AD group in which the user is in? Can anyone help?

---

