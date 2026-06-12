---
title: "Recently Installed Ubuntu 13.04 and having issues"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by nothingwillgowrong on 2013-09-01
I was told to make another thread here since a large portion of my issues relate to the speed of my wireless network.

Original thread detailing the many issues I'm having with 13.04 is [URL="http://ubuntuforums.org/showthread.php?t=2171485&page=2&p=12776174#post12776174"]HERE

[/URL]> Quick Summary of my Internet Related Problems

-It's **extremely slow:** Speed Test [RESULTS]("http://www.speedtest.net/my-result/2937170325").
-Nothing else on my network is even remotely this slow such as an adjacent Laptop with lower specs: Speed Test [RESULTS]("http://www.speedtest.net/my-result/2937024577")
-Removing other devices from network does not improve the speed nor does resetting my modem or router.
-The specs of this computer can be found at the start of my original problem thread.

Any ideas?

A huge part of the reason I'm having difficulty trouble shooting all my other issues with Ubuntu is that the download rate is so slow that it takes hours just to get simple drivers that may or may not fix issues I'm having in other areas which is why I consider the network speed to be a high priority.

Will provide additional information on request/as necessary.

Thanks in advance.

EDIT: I do not have access to a wire connection.

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

### Post by nothingwillgowrong on 2013-09-01
Stupid question but do I have to be connected to my wireless network when I run the script or can I be connected to the ethernet the wireless runs off of? 

I moved the PC upstairs and attached it to ethernet (turns out I had a cable after all) and it is running at a much faster rate.
 
Obviously I'd like to fix the wireless so I do not have to keep it here though.

The file was created as a .txt file so I renamed the extension to .txt.tar.gz and uploaded it.

---

### Post by wildmanne39 on 2013-09-01
It would be best to be using the wireless when you run the script without the ethernet plugged in.

The file you attached will not open if it does not zip the file itself then you just attach the file it created as is.
Thanks

---

### Post by nothingwillgowrong on 2013-09-01
> **Wild Man said:**
> It would be best to be using the wireless when you run the script without the ethernet plugged in.

The file you attached will not open if it does not zip the file itself then you just attach the file it created as is.
Thanks

Ok I'll see what I can do. 

At this point I'd like to point out the only remaining issue is the wireless and the "AMD Unsupported Hardware" watermark at the bottom right of my screen. I'll make a post in my previous thread saying it can be closed.

---

### Post by nothingwillgowrong on 2013-09-01
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

Ok I was kind of confused about the whole zipping part so I uploaded the .txt file this time. I'm sorry I'm new to Ubuntu.. :/ Does it have to be zipped? How do you do it? When I right click on the file I didn't see any obvious way of zipping it like in Windows or something.

At this point I'd also like to point out I fixed the AMD UNSUPPORTED HARDWARE watermark, so literally everything else is now working properly except the wireless.

---

### Post by wildmanne39 on 2013-09-01
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Also set your wireless setting to match the screenshots.
Thanks

---

### Post by nothingwillgowrong on 2013-09-01
> **Wild Man said:**
> Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Also set your wireless setting to match the screenshots.
Thanks

Did as you ask and performed a speed test. I noticed that the speed occasionally bounced up to normal speed as opposed to before where it was completely stuck at low speeds. Overall speed still seems to problematic though.

[Here are the results.]("http://www.speedtest.net/my-result/2938697135")

---

### Post by wildmanne39 on 2013-09-01
What is the speed of your isp?

---

### Post by nothingwillgowrong on 2013-09-01
> **Wild Man said:**
> What is the speed of your isp?

[Speed Test for a nearby laptop using the same network.]("http://www.speedtest.net/my-result/2937024577")

I've used other computers and laptops on this network before and they all tend to get in or around this speed.

EDIT: [Speed Test for this computer but using Ethernet instead of wireless.]("http://www.speedtest.net/my-result/2938707328")

---

### Post by wildmanne39 on 2013-09-01
A couple of things you are using the wrong driver for your ethernet so if it is plugged in you will get slow connections because the ethernet connection overrides the wifi connection.

Also your encryption in the router is CCMP TKIP can you change that to CCMP AES or CCMP only? there is a bug that is causing the slow down when using the TKIP and it is shown in your information that you posted.
Thanks

---

### Post by nothingwillgowrong on 2013-09-01
> **Wild Man said:**
> A couple of things you are using the wrong driver for your ethernet so if it is plugged in you will get slow connections because the ethernet connection overrides the wifi connection.

Also your encryption in the router is CCMP TKIP can you change that to CCMP AES or CCMP only? there is a bug that is causing the slow down when using the TKIP and it is shown in your information that you posted.
Thanks

The ethernet is not ordinarily plugged in when I am using the wireless, and the speed issues are definitely their when the wireless is used whether or not I have ethernet plugged in.

Where can I install the latest drivers for my wireless?

Also I hate to ask but are their any good resources on how to change the router encryption? I have no idea. Also would it affect my other devices such as a Laptop? 

Thanks for all your help.

EDIT: Changed it from "WPA-TKIP or WPA2-AES" to just "AES" and that fixed it.

I'll give it a bit and post back if any further issues are caused. 

Thanks a ton!

---

### Post by wildmanne39 on 2013-09-01
With the driver that you are using it usually is not a benefit to manually install a newer driver.

I am glad that worked, I thought it would after I saw the error message.

Please mark as solved if it continues to work.
Thanks

---

