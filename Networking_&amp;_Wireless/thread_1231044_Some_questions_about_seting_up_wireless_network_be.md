---
title: "Some questions about seting up wireless network between linux and vista ;"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by a.dehqan on 2009-08-04
In The Name Of God
I'll be thankfull if you guide ;

Some questions about seting up wireless network between linux(debian base) and vista ;

1-These steps have been done in linux:
ifconfig wlan0 down
/etc/dbus-1/event.d/25NetworkManager stop
iwconfig wlan0 mode ad-hoc
iwconfig wlan0 channel 6
iwconfig wlan0 essid allah
iwconfig wlan0 key 12346
ifconfig wlan0 up
ifconfig wlan0 192.168.0.1

This command set a key ,what is it encryption type ?WEP ?

2-On other side(vista),what type of athentication should be set ? no athentication ? shared ? WAP2-personal ?

3-With which command ,will linux connect to the network that vista is waiting in it ?

4-Should encryption type on each side be similar ?

5- With wifi-radar linux connects but it does not show any shared folder of vista just there is a icon with the name of vista computer .

6- Can network be setup without any encryption and security types ?

Regards dehqan

---

### Post by superprash2003 on 2009-08-04
i think its WEP.. other sie WEP as well.. if you created a adhoc with vista then it should show up under **sudo iwlist scanning** .. yes similar encryption..make sure both machines can ping each other for shared folders..
 yes network can be setup without encryption as well

---

### Post by a.dehqan on 2009-08-04
In The Name Of God The compassion merciful

Thanks alot for your attention ;

1-When fisrt ad-hoc is set in vista ,should be all these steps done in linux :

ifconfig wlan0 down
/etc/dbus-1/event.d/25NetworkManager stop
iwconfig wlan0 mode ad-hoc
iwconfig wlan0 channel 6
iwconfig wlan0 essid allah
iwconfig wlan0 key 12346
ifconfig wlan0 up
ifconfig wlan0 192.168.0.1

2- Can channel be set anyone of numbers 1-13 ? Or channel is specified
by adaptor ?

3-First in vista ad-hoc wireless network has been created then in
linux after runnig above command ,linux has been connected to vista
but yet linux does not show vista shared folders ,what is/are the
reason/s ?

4-To see vista shared folders in linux just adding workgroup name in smb.conf is enoughe ?

regards dehqan

---

### Post by superprash2003 on 2009-08-05
does this have a GUI network manager? it would be easier than typing those commands. but yes those commands are required

2)any channel would work
3)are the two machines able to ping each other first?
4)not required thoiugh

---

