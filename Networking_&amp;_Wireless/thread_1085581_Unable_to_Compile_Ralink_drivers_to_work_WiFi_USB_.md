---
title: "Unable to Compile Ralink drivers to work WiFi USB Adaptor"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by mixtri on 2009-03-03
Please Help!!

I bought a wifi usb adapter: SParklan N series with Linux drivers provided at the manufacturers website.

The Linux drivers need to be compiled on a PC. I have tried doing this by following instructions to download, save and unpack drivers to a folder in my home directory. Switch to the folder in a terminal and run the "Make" command.

I get errors when running this command - see attached text file below: ([COLOR="Red"]The link doesn't work please see next post for details[/COLOR])

I do not understand the intricacies of compile time errors and how to fix them. I was hoping someone here with the knowledge would be kind enough to have a look at the errors generated and maybe, hopefully offer a up a solution.

I'm running Ubuntu 8.10 on an AMD64 bit based HP pavilion dv7-1132nr laptop.

I thought it would be better if I checked and made sure before going back to the manufacturers that the problem wasn't generated as a result of the Ubuntu OS but possibly that of the Linux wireless drivers provided by the manufacturer. I'm inclined to go with the latter case in this scenario.

Anyone attempting to solve this, may need to acquire the drivers and then test them on their machines. Here is the link to the drivers: [Link]("http://www.sparklan.com/download.php?support_id=165") (Click on the link for Linux Drivers).

Also,there are configuration instructions that will need to be carried out prior to compiling. The instructions are located in the "README" file. 

Thanks very much in advance.

---

### Post by mixtri on 2009-03-03
Sorry about this guys For some odd reason I can't get the attachment to link to this page. I'll just paste the terminal results below instead.

albert@albert-laptop:~$ cd Downloads
albert@albert-laptop:~/Downloads$ cd ./2008_0528_RT2870_Linux_STA_v1.3.0.0 
albert@albert-laptop:~/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0$ make
make -C tools
make[1]: Entering directory `/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/tools'
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/md5.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/mlme.o
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/mlme.c: In function &#8216;BssEntrySet&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/mlme.c:3633: warning: unused variable &#8216;idx&#8217;
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/action.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/ba_action.o
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/ba_action.c:1427: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.o
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:555: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:557: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:641: warning: assignment makes integer from pointer without a cast
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;update_os_packet_info&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:663: warning: assignment makes integer from pointer without a cast
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:683: warning: assignment makes integer from pointer without a cast
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:883: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:930: warning: assignment makes integer from pointer without a cast
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_linux.c:938: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_main_dev.o
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;rt_ieee80211_if_setup&#8217;:
/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_main_dev.c:788: error: &#8216;struct net_device&#8217; has no member named &#8216;nd_net&#8217;
make[2]: *** [/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/../../os/linux/rt_main_dev.o] Error 1
make[1]: *** [_module_/home/albert/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [LINUX] Error 2
albert@albert-laptop:~/Downloads/2008_0528_RT2870_Linux_STA_v1.3.0.0$

thanks

---

### Post by mixtri on 2009-03-05
I have managed to solve the problems mentioned above by obtaining correct drivers from the Ralink website. i am now up and running full throttle. WeyHey!
Send me a private message if you need any help as I shall not be accessing this thread any longer.:D

---

### Post by mixtri on 2009-03-05
see above

---

