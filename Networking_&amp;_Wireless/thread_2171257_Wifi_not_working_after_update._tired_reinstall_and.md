---
title: "Wifi not working after update. tired reinstall and then update- didnt work"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by vmarcano718 on 2013-08-29
Help please.

wifi not working after update- i can see routers but cant connect.

initially, i tired googling the answer and followed some posts. didnt work out. reinstalled ubuntu and updated again and had the same problem. eth0 works. using it now.

---

### Post by wildmanne39 on 2013-08-29
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by dhunt84971 on 2013-08-29
Can you verify that the security settings you are using to connect to the Wifi router matches the router's settings (e.g. WPA, WEP)?  Also, make sure that you have your IPv4 and IPv6 settings set for Automatic (DHCP) if this is appropriate.  When you say you cannot connect, are you getting an error?  You could also try Editting your connections and removing all of the registered Wifi connections, so that you will be given the chance to log back in again, in the case that a bad setting has been previously associated with the connection.

---

### Post by vmarcano718 on 2013-08-29
Here you go.

---

### Post by vmarcano718 on 2013-08-29
this is with the eth0 plugged in.

---

### Post by wildmanne39 on 2013-08-29
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Does that make it connect? if not is EChavez the network you want to connect too?

Thanks

---

### Post by vmarcano718 on 2013-08-29
Can you verify that the security settings you are using to connect to the Wifi router matches the router's settings (e.g. WPA, WEP)?

**Yes. It was working before the update. After the update there was no changes on my part. I double checked.**

  Also, make sure that you have your IPv4 and IPv6 settings set for Automatic (DHCP) if this is appropriate. 

**Yes. First thing i checked.**

 When you say you cannot connect, are you getting an error?  You could also try Editting your connections and removing all of the registered Wifi connections, so that you will be given the chance to log back in again, in the case that a bad setting has been previously associated with the connection.

**Tired this. Didnt work either.**

---

### Post by vmarcano718 on 2013-08-29
> **Wild Man said:**
> Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Does that make it connect? if not is EChavez the network you want to connect too?

Thanks

Here is the requested information after a reset and without connecting eth0.

The terminal commands you gave me did not work. I am tying to connect to 'Loading...'

---

### Post by wildmanne39 on 2013-08-29
Did you watch the out put of the commands I ask you to run to see if they completed correctly?

Please post the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
I would remove the periods after your network name linux does not like strange characters.

Also it is a nightmare for network manager to connect to a network because there are so many in range of your computer and many are on the same channel.

Do you need the computer to connect to different networks if not we could try a static ip.
Thanks

---

### Post by vmarcano718 on 2013-08-29
IT TOOK A SECOND BUT IT WORKS!! Can you tell me what was the problem.

---

### Post by wildmanne39 on 2013-08-29
What did you do after your last post?

---

### Post by vmarcano718 on 2013-08-29
> **wild man said:**
> what did you do after your last post?

nothing it just took a second to connect.

What you did worked.

---

### Post by wildmanne39 on 2013-08-29
In that case, the commands you ran change the encryption from the hardware to software sometime it works better that way depending on the driver and brand of device, other times it works best with the encryption handled by the hardware.

Please use thread tools and mark the thread solved.
Enjoy!

---

### Post by vmarcano718 on 2013-08-29
> **Wild Man said:**
> Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Does that make it connect? if not is EChavez the network you want to connect too?

Thanks

I see. i reread your code:

no hw encrpt as an option. in a configuration file.

---

