---
title: "Intel537EP problems....."
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by nrayever on 2006-02-09
hi everyone:

i manage to install and run 2 modems with chipset Intel537EP, one for each pc. but i got a problem and i don't know how to solve it. the problem is that i don't really know how to set a symlink or hardlink for the modem in /dev.

i used this documentation from wiki.ubuntu
[HTML]https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4[/HTML]
to install the modem driver. i know that this documentaion is for Intel536EP, but making some deep thinking, i manage to install the driver. the driver for Intel537EP is avaliable here:

[HTML]http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9288&strOSs=39&OSFullName=Linux*&lang=eng[/HTML]
this driver is for suse, yes indeed. but work with ubuntu and the documentation from wiki.ubuntu.

when i was looking for the modem in /dev, i have found that a new device was created named as "Intel5370" ( so obvious!!). so i manage to make a connection with my isp but using System / Administration / Network tool to connect.

most of Xppp programs (Kppp, Gnome-ppp, etc.....) has on their devices list:

Example:

/dev/modem
/dev/tty
etc.... 

so i tried to make a symlink from /dev/Intel5370 to /dev/modem, so Xppp apps can use the Intel537EP modem as /dev/modem.

i used the command ```
sudo ln -s /dev/Intel5370 /dev/modem
```

and that worked pretty cool!, but when i rebooted the pc's the symlink was gone. my question is:

is there any way to make a symlink permanet?? or should i use a hardlink?? in any case, how should i do it?? i don't have a clue to do it, please any help would be appreciated!!!

sincerly nrayever

---

### Post by ddtmsa on 2006-02-09
Hi nrayever,

After you created the symbolic link, were you able to go online successfully?

If the answer is no, then I could make some suggestions as I've managed to get an Intel537ep modem to work successfully in breezy.

If you did manage to get online, then firstly congratulations. But I cannot answer your question, however I would suggest that this is the wrong forum to ask for help. Your problem is nothing to do with networking but with the system, try reposting in the Desktop Support forum. 

You would also be advised to rename your thread to something along the lines "Disappearing symbolic links".There are many, many posts on getting winmodems to work and I for one have just about given up trawling through all the posts. You can get winmodems to work, but it takes a bit of knowledge about unix/linux and alot of new users don't have the patience to learn.

---

### Post by nrayever on 2006-02-09
[QUOTE=ddtmsa]Hi nrayever,

After you created the symbolic link, were you able to go online successfully?

If the answer is no, then I could make some suggestions as I've managed to get an Intel537ep modem to work successfully in breezy.

If you did manage to get online, then firstly congratulations. But I cannot answer your question, however I would suggest that this is the wrong forum to ask for help. Your problem is nothing to do with networking but with the system, try reposting in the Desktop Support forum. 

You would also be advised to rename your thread to something along the lines "Disappearing symbolic links".There are many, many posts on getting winmodems to work and I for one have just about given up trawling through all the posts. You can get winmodems to work, but it takes a bit of knowledge about unix/linux and alot of new users don't have the patience to learn.[/QUOTE]

hi ddtmsa:

i have successfully got online with this modem in two different machines that have them. and thanks for your advise maybe i should try in another zone of the forum.

nrayever

---

### Post by Matchless on 2006-02-11
Hi,
   I have updated the wiki DialupModemHowto with the symlink part for the Intel536 today. This should help you.

---

