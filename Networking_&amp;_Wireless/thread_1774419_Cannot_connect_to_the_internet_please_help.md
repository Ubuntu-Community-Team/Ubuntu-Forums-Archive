---
title: "Cannot connect to the internet please help"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by Adnaan1 on 2011-06-03
hello there im new to linux and i cant connect to the internet, when i am about to connect to the internet its says you are now offline, then when I put my WPA key in and it starts to connect and when its finished connecting it says you are now offline again, the network name comes up but i cant connect :confused:

---

### Post by nos09 on 2011-06-03
> **Adnaan1 said:**
> hello there im new to linux and i cant connect to the internet, when i am about to connect to the internet its says you are now offline, then when I put my WPA key in and it starts to connect and when its finished connecting it says you are now offline again, the network name comes up but i cant connect :confused:

what kind of modem you are usimg please specify.

---

### Post by Adnaan1 on 2011-06-03
I am not using a modem its a wirless usb reciever called 
 
Realtek RTL8188SU LAN 802.11n USB 2.0 Network Adapter

---

### Post by nos09 on 2011-06-03
> **Adnaan1 said:**
> I am not using a modem its a wirless usb reciever called 
 
Realtek RTL8188SU LAN 802.11n USB 2.0 Network Adapter

[http://ubuntuforums.org/showthread.php?p=9960924](http://ubuntuforums.org/showthread.php?p=9960924)

i think this would help.. i found it on google. but i didnt read it, i would but i have to go to class.. good luck.

---

### Post by Adnaan1 on 2011-06-03
Thanks anyway for the effort &#2343;&#2344;&#2381;&#2351;&#2357;&#2366;&#2342; &#1588;&#1705;&#1585;&#1740;&#1729;

---

### Post by Adnaan1 on 2011-06-03
please can someone else help

---

### Post by Joe of loath on 2011-06-03
The thread linked should work.

---

### Post by Adnaan1 on 2011-06-03
Its too complicated can you please help me

---

### Post by Joe of loath on 2011-06-03
What do you want me to help you with? Just do what the instructions say.

---

### Post by slooksterpsv on 2011-06-03
Do the following in terminal:

```

wget -c ftp://202.134.71.22/cn/wlan/RTL8188SU_usb_linux_v2.6.0006.20100625.zip
tar zxcf ./RTL8188SU_usb_linux_v2.6.0006.20100625.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20100625
make

```

If you get any errors at this point let us know (you'll see like make-error #2 or that), otherwise continue.

```

./clean
gksudo insmod 8712u.ko
gksudo cp ./8712u.ko /lib/firmware

```

If you get any errors with the above, let us know before continuing.

```

gksudo cp /etc/rc.local ~
sed 's/exit 0/insmod \/lib\/firmware\/8712u.ko &/' < ~/rc.local > ~/rc.local.tmp
echo "exit 0" | gksudo tee -a ~/rc.local.tmp
gksudo mv /etc/rc.local /etc/rc.local.bak
gksudo mv ~/rc.local.tmp /etc/rc.local
gksudo rm ~/rc.local

```

That should do it =D, if anyone sees any errors in what I pasted above let me know.

---

### Post by Adnaan1 on 2011-06-03
[EMAIL="buntu@ubuntu:~$"]buntu@ubuntu:~$[/EMAIL] sed 's/exit 0/insmod \/lib\/firmware\/8712u.ko &/' < ~/rc.local > ~/rc.local.tmp
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] echo "exit 0" | gksudo tee -a ~/rc.local.tmp

bash: cd: rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20100625: No such file or director
 
thats whats i get

---

### Post by Joe of loath on 2011-06-03
That means you're in the wrong directory, or the folder isn't called that. try cd rtl*.

---

### Post by Adnaan1 on 2011-06-03
Ive tried doing that plus im running ubuntu off a usb like a live cd
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] wget -c [ftp://202.134.71.22/cn/wlan/RTL8188SU_usb_linux_v2.6.0006.20100625.zip](ftp://202.134.71.22/cn/wlan/RTL8188SU_usb_linux_v2.6.0006.20100625.zip)
--2011-06-03 16:57:32--  [ftp://202.134.71.22/cn/wlan/RTL8188SU_usb_linux_v2.6.0006.20100625.zip](ftp://202.134.71.22/cn/wlan/RTL8188SU_usb_linux_v2.6.0006.20100625.zip)
           => `RTL8188SU_usb_linux_v2.6.0006.20100625.zip'
Connecting to 202.134.71.22:21... failed: Network is unreachable.
tar: You may not specify more than one `-Acdtrux' or `--test-label' option
Try `tar --help' or `tar --usage' for more information.

---

### Post by Joe of loath on 2011-06-03
Do you have an internet connection?

---

### Post by Adnaan1 on 2011-06-03
if your asking if i can connect on my ubuntu no but if your asking if have i got internet yes sure on my windows computer every thing works fine and it works no problems what so ever the network comes up on the network list but i cant connect to it

---

### Post by Joe of loath on 2011-06-03
Well, you can't download stuff from the internet using wget without a connection :p Download the file in Windows, copy it over, and follow the rest of the instructions.

---

### Post by Adnaan1 on 2011-06-03
what instructions the ones that come with the driver

---

### Post by nos09 on 2011-06-03
> **Adnaan1 said:**
> what instructions the ones that come with the driver

the instruction that we have told you or the one that comes with the package what ever you feel comfortable with..

---

### Post by nos09 on 2011-06-03
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=3&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=3&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true)

i found the drivers that should work with your device. read the README file or the INSTALL files for guidance.

---

