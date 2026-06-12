---
title: "having wifi issues with both Ubuntu 13.04 and 12.04"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by RedPiano on 2013-08-29
Hello all,

I am new to ubuntu. I recently decided to try Ubuntu because my CSCI teacher recommended me to use a Unix environment in order to program with GCC.

I currently own an Asus: Asia ME301T.

I originally downloaded Ubuntu 13.04, but when trying to connect to the wifi, it would simply attempt to connect, and continue thinking until a "Disconnected from wifi" gui pops up. I searched the forums and saw others with similar problems on a laptop with 13.04 and there seems to be no solution.

I eventually downgraded to 12.04 in hopes to fix this problem, and I am basically getting the same problem except now it actually prompts me for the password, attempts to connect, then fails and keeps prompting me for the password. This will happen continuously until I turn the wifi off. If i turn it back on it continues. 

Can anyone help? 

Ask away if you have any questions.

Thanks!

---

### Post by RedPiano on 2013-08-29
bump

---

### Post by wildmanne39 on 2013-08-29
Please be patient! as per the CoC only bump once every 24 hours.
Thanks

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

### Post by RedPiano on 2013-08-29
ok will do. I will post as fast as I can

---

### Post by RedPiano on 2013-08-29
Ok. During step 2 in the link you provided, nothing happens when I click "Run".

Is there maybe something I am missing/doing wrong?

---

### Post by wildmanne39 on 2013-08-29
If, however, you can't connect via cable, you can download the script on another computer by right-clicking this link, and choose to "Save" the link target. Copy the downloaded file to your Ubuntu machine and run it from there as follows -

1) Right-click the downloaded file, click "Properties" and go to "Permissions" tab. There, tick the "Execute" checkbox to make it executable, then close the box.

2) Now double-click the file and select "Run" in the opened dialogue box. Provide your password when asked.
[NOTE : In 13.04, the default behaviour is to open the file as text even when it is made executable. To change this, please open any folder > go to "Files > Preferences > Behaviour" tab, and select "Ask each time" option under "Executable Text Files" section.]

3) A fresh new file named "wireless-info.txt" (or "wireless-info.txt.tar.gz" file, if the text file size exceeds 19.5 KB) will be created in the same directory where you have run the script from. Attach it or copy-paste its contents (as described above) in your next post.

---

### Post by RedPiano on 2013-08-30
Yes, but during step 2) once i click "Run" nothing happens.

---

### Post by RedPiano on 2013-08-30
ok i deleted the file then tried it again and this is what I got:
[file:///C:/Users/Josh/Desktop/wireless-info.txt](file:///C:/Users/Josh/Desktop/wireless-info.txt)

---

### Post by wildmanne39 on 2013-08-30
Are you running this when booted into ubuntu? if so why does it show a C: drive?

Did you copy the file to ubuntu?

I have never seen anyone have trouble with the script so this is new to me as well.

Did you do this? > In 13.04, the default behaviour is to open the file as text even when it is made executable. To change this, please open any folder > go to "Files > Preferences > Behaviour" tab, and select "Ask each time" option under "Executable Text Files" section.
Thanks

---

### Post by RedPiano on 2013-08-30
I am running windows 7 and 12.04 now. I no longer have 13.04. I coppied it from a flash drive from windows and rebooted and switched to Ubuntu. From there I downloaded the file from my flash drive.

See my previous post for feedback from the code in the file I was told to execute.

---

### Post by RedPiano on 2013-08-30
Yes it is working now. I copied the file from windows 7 on to a flash drive then immediately switched to Ubuntu and executed it there.

I do not see a C drive in Ubuntu, but I will check again to see. 

Was the attachment in my previous post any helpful to you?

---

### Post by RedPiano on 2013-08-30
Oh and I think the reason it might show a c drive is because after the wireless_info.txt was created in Ubuntu, I uploaded it then BACK onto my flash drive then reopened windows (where my wifi is still working) and attached it to the forums from there.

---

### Post by wildmanne39 on 2013-08-30
No the file is not click-able, I can not open it but if you changed from 13.04 to 12.04 then I will need the file from the 12.04 version.
Thanks

---

### Post by RedPiano on 2013-08-30
hmm ok. it seems to be working for my laptop, but not on the browser on my tablet. I would copy and paste it but it is too large. Is there some other website that you would know of that I can share text with?

---

### Post by RedPiano on 2013-08-30
Here is a link to a pastie.org page containing the wireless_data text that you asked for!

I hope this helps. If you need me to try to send it a different way, let me know

[http://pastie.org/8284763](http://pastie.org/8284763)

---

### Post by brandon10 on 2013-08-30
Hello guys im having the same problem. whats happening is that the dhcp is not automatically pulling the ip address. now im new to linux myself. the only way i can get my laptop to connect to the internet wireless is by me entering the ip address along with subnet mass and default gateway. im trying to find a solution myself

---

### Post by wildmanne39 on 2013-08-30
Please try:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless
```
Reboot does it connect if not please paste the whole file to [http://pastebin.com/](http://pastebin.com/) because a lot of the file was cut off.
Thanks

---

### Post by varunendra on 2013-08-31
> **RedPiano said:**
> ok i deleted the file then tried it again and this is what I got:
[file:///C:/Users/Josh/Desktop/wireless-info.txt](file:///C:/Users/Josh/Desktop/wireless-info.txt)
"file:///...." type addresses are local addresses. Means it is a location on your computer and will ONLY work on that same computer.
The best option is to open the file > copy the whole content > paste it on [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) > copy the URL of the page that comes up after pasting (submitting) the contents > paste that URL in your next post.

Alternatively, you can attach the file itself in your next post using the paperclip button at the top of edit box in which you create new posts.
Make sure the file is complete. It should end with the line - "****************** done ******************". If your "wireless-info.txt" file does not have that line at its bottom, it is incomplete.

> **brandon10 said:**
> Hello guys im having the same problem. whats happening is that the dhcp is not automatically pulling the ip address. now im new to linux myself. the only way i can get my laptop to connect to the internet wireless is by me entering the ip address along with subnet mass and default gateway. im trying to find a solution myself
Welcome to the forums brandon10 !

Wireless issues are very subjective and can be different for different people, even if the symptoms look the same. As such, unless you are absolutely sure that your card and driver and the pertaining issue are exactly same, I'd suggest you start a new thread of your own and post the details of your problem there.

---

