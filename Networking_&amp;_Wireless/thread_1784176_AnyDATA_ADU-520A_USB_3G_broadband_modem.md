---
title: "AnyDATA ADU-520A USB 3G broadband modem"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Antonio Pedro on 2011-06-16
Hi everyone! I'm trying to use in Ubuntu 11.04 / Trisquel 4.5.1 my ** AnyDATA ADU-520A** USB 3G broadband Internet modem, but i'm having  trouble. The device is detected but when i try to connect nothing  happens.

My ISP provides an install and connect script  ([http://www.zapp.pt/c/document_library/get_file?uuid=2c8fe21a-86db-4a27-96a8-03cb66542a06&groupId=10209](http://www.zapp.pt/c/document_library/get_file?uuid=2c8fe21a-86db-4a27-96a8-03cb66542a06&groupId=10209))  but it's for a different model; i've tried it anyway but it doesn't  work. The modem manufacturer provides support for MAC and Windows ([http://www.anydata.com/Support.html](http://www.anydata.com/Support.html)), but not for Linux. :evil:

Following some tips available througout the Internet, i've tried to edit **/etc/ppp/chap-secrets**, **/etc/ppp/pap-secrets** and some other related files that i don't remember at the moment, but that didn't help either. 

I also tried, in Trisquel, to use wvdial, wvdialconf and have configured **/etc/wvdial.conf** file... after a few seconds i get a message saying that the modem isn't respondig. I'm not sure if the dial commands are allright, but i've inserted them as they are in the script that my ISP provides  ([http://www.zapp.pt/c/document_library/get_file?uuid=2c8fe21a-86db-4a27-96a8-03cb66542a06&groupId=10209](http://www.zapp.pt/c/document_library/get_file?uuid=2c8fe21a-86db-4a27-96a8-03cb66542a06&groupId=10209)). I followed the 2nd method (without installing any additional software/package/file), as explained here: [http://trisquel.info/en/wiki/configure-3g-modem](http://trisquel.info/en/wiki/configure-3g-modem); but, as i said before, it didn't work.

I'm going insane with this one. Shouldn't the network manager be able to handle this? I need a follow-through with this. Can anyone help me, please? [-o<

---

### Post by jmlm-1970 on 2011-07-26
Well according to what you say, the only missing is the options file and wvdial file...

Try this for those files:

/etc/ppp/options
# empty file

/etc/ppp/peers/wvdial
noauth
name wvdial
usepeerdns

/etc/resolv.conf
nameserver 10.5.1.10
nameserver 10.5.1.11
search home

Now wvdial should work, if not put baud at 9600, dial #777, stupid mode at 1 in the file /etc/wvdial.conf... And try wvdial, if fails, just restart and try again, it should work with these settings...

If you have still problem, just contact me here or to multi.jmlm_1970 at hotmail.com

---

