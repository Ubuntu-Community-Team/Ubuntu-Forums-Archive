---
title: "cannot connect to wifi hotspot"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by halfhearted on 2013-04-16
I'm using 12.10 on a Samsung Q45 laptop and cannot connect to one specific wifi hotspot where I work. This is the only hotspot that I cannot connect to. Every other hotspot I can connect to without any problem. If I use my Win7 Pro (64bit) laptop with my work hotspot then it connects immediately. Nobody else (they all use windows) has any problems connecting to the work hotspot. I don't get an error message, all that happens is that 12.10 attempts to connect and eventually gives up. I never get as far as inputting a username and password. I have absolutely no idea why this is happening. If I knew why the failure was happening I might be able to fix it. I'd appreciate some help if anyone's got any ideas. Thanks in advance.

---

### Post by halfhearted on 2013-04-18
Help?

---

### Post by wildmanne39 on 2013-04-18
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by halfhearted on 2013-04-19
OK Wild Man. Thanks. I will run the command. I assume I should do this when the laptop is actually trying to connect to the problem wifi hotspot (at work) rather than when using the laptop (like now) at home. Or doesn't it matter?

---

### Post by wildmanne39 on 2013-04-19
Yes it needs to be the one you are having problems connecting too.
Thanks

---

### Post by halfhearted on 2013-04-21
Right. I'll do it tomorrow at work and post the output.

---

### Post by halfhearted on 2013-04-22
Hi Wild Man, I tried to attached the netinfo.txt file that your wifi script output but it exceeded the size limit for attachments for the forum. Next I tried to simply cut and past the contents of netinfo.txt. I received this error message -

"You have included a total of 87 images in your message. The maximum number that you may include is 8. Please correct the problem and then continue again. Images include use of smilies, the BB code [img] tag, and HTML <img> tags. The use of these is all subject to them being enabled by the administrator."

Obviously there are no images in the text and I have removed all the brackets that look like < > [ ]. I do not understand the error message. Please help.

---

### Post by halfhearted on 2013-04-22
It worked this time. I used .odt format.

---

### Post by wildmanne39 on 2013-04-22
I am on my cell phone right now I will take a look as soon as I get home if someone does not beat me to it.

---

### Post by wildmanne39 on 2013-04-22
One issue is that with all those networks at work most of them have only two names so network manager jumps from one to the other not knowing which one to connect too.

Second linux drivers connect best with wpa2 AES only encryption.

If you have not added this option already please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
What is the name of the network you want to connect too?
Thanks

---

### Post by halfhearted on 2013-04-23
Thanks for suggestions so far. The network is pdc-gu.

---

### Post by halfhearted on 2013-04-29
Wild Man, I tried entering the commands -
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
as you suggested but they didn't help. I still couldn't connect to the wifi network
pdc-gu. One consequence of the first command was that it prevented me from connecting to my own home wifi which is configured to broadcast on 802.11n only. So I solved that by entering -
echo "options iwlwifi 11n_disable=0" | sudo tee /etc/modprobe.d/iwlwifi.conf
which turned it back on. Thanks for help so far. Does anyone have any more ideas?

---

### Post by halfhearted on 2013-05-02
Anyone got any ideas why I can't connect to this particular wifi network?

---

