---
title: "Lenovo thinkpad l430 wifi breaks after 2-3 min"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by abhinav_dora on 2013-09-01
hi

i am using lenovo l430 and its wifi gets disconneted after 5-10 min,i checked pinging my wifi router ip it gives "ping: sendmsg: Network is unreachable"
 when it gets disconnected,on the other hand it works fine in my office wifi plz help asap.

---

### Post by wildmanne39 on 2013-09-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by abhinav_dora on 2013-09-01
hi 

plz find the attachment.

---

### Post by wildmanne39 on 2013-09-01
This driver is a problem in linux, have you added any driver parameters to it already? or installed the driver manually?

According to the information you posted it looks like your firewall is blocking the connection, so change the firewall settings first and see if that helps or deactivate it completely for a little while to test this theory.

If you have issues with the firewall deactivated post a new wireless file so we can see what is going on with it disabled.

Also change encryption in your router to just wpa2 if you have that option, wep is weak and does not work the best with linux drivers.

You will also need to go to network manager top right corner of the screen and click on edit connection>wireless and change security to wpa/wpa2.
Thanks

---

### Post by praseodym on 2013-09-01
Please try the following module parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

---

### Post by abhinav_dora on 2013-09-02
hi

i have turned off firewall,also their is no external driver installed.
my modem doesnt support wap2 ,so i cant change it.
plz find attached wireless script after firewall was turned off.

now situation it that its connecting for only few sec and then disconnects

---

### Post by abhinav_dora on 2013-09-02
hi 
i didnt help i think it had made situation even worst ,plz help in resolving it

---

### Post by praseodym on 2013-09-02
You need to run the script via

```
./wireless_script
```

not copying the script itself ;)

---

### Post by abhinav_dora on 2013-09-04
hi plz find the scipt

---

### Post by praseodym on 2013-09-04
Open the file
```

gksudo gedit /etc/network/interfaces
```
remove "eth0" only, save, close and reboot

---

