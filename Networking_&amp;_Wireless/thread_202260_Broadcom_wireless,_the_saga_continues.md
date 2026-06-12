---
title: "Broadcom wireless, the saga continues"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by Bytewalker on 2006-06-23
Okay i cant get the wireless working and im totally stmped now, i went through the entire procedure at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29)

so this is what ive done so far:

apt-get installd ndiswrapper, ndis-utils and ndisgtk

lspci -n shows the broadcom as 14e4:4320, corresponding to bcmwl5a.inf as the correct file to get (i got bcmwl5 too though)

downloaded the then extratd .inf/.sys files

so i did 
ndiswrapper -i on the .inf files
then
ndiswrapper -l shows bcmwl5a as driver present, hardware present
then i do
ndiswrapper -d 14e4:4320 bcmwl5a

modprobe ndiswrapper

then "ifup wlan0" brings up this crazy error (i even ifdown'd eth0 before trying this):
>SIOCSIFADDR: No such device
>Bind socket to interface: No such device
>Failed to bring up wlan0.

the ONE thing i think it might be that some1 else mentioned is a conflict with anotehr device (one that doesnt work) thats stopping ndis from being used.. but i cant find anything on how to find this device or disable..

any thoughts greatly appreciated thanks in advance!!!

---

