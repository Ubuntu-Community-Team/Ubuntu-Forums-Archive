---
title: "Ubuntu keeps getting kicked off wifi"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by Jt00 on 2012-08-16
Ubuntu keeps getting kicked off of my home wifi. I am very confused about this because it is on a triple boot system, and on Windows 7 I have no problems with wifi (I don't use Backtrack online). But on Ubuntu I get a good connection when I boot into Ubuntu, then after a few minutes I try to go to a web page and it stalls. If I let it keep going it says the server at www.<website I was trying to visit>.com could not be found. Then I lose my wifi connection, and no matter how many times I enter the correct password, Ubuntu takes it, tries to get back on the wifi, and comes back asking for the password. It does this even if I just disconnect from the wifi (asking for wifi password). It is very annoying to have to go to Windows for internet, so is there a fix for this?
This is on a Toshiba Satellite l855-s5280p with a Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC.

---

### Post by wildmanne39 on 2012-08-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Jt00 on 2012-08-17
After failing to edit the script to save to a different file, I ended up just having to do some cutting and pasting because netinfo.txt kept getting overwritten.
Anyway, I ran the script multiple times and saved two of the output files.

Netinfo.txt is the output when first booted up. The wifi is connected.

Netinfo1.txt is right after the connection is dropped.

---

### Post by wildmanne39 on 2012-08-18
Hi, please do what is at this link in post #6.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Thanks

---

### Post by Jt00 on 2012-08-20
Thanks, that seems to have fixed it! It could break down again right after I post this for all I know, but for now, it works great!
Just out of curiosity, what did the file I created do?

---

### Post by wildmanne39 on 2012-08-20
Hi, glad it is working! The file changed the encryption from hardware to software.
Thanks

---

### Post by frank cox on 2012-10-11
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

Thanks-will let you know how it went.

---

### Post by frank cox on 2012-10-11
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks


Here are the files it created,thanks. I had to copy / paste the wireless-script file into gedit and save it as wireless-script .txt  because it would not upload as it was.
Wireless is unchanged, not working.

---

