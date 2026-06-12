---
title: "Wireless network: &quot;device not ready (firmware missing)&quot;"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by martin_385 on 2011-06-12
Hi!

I have installed Ubuntu 11.04 on my laptop. For some reason Wireless Network does not work any more (there was installed 9.04 before).

lspci says:
```

00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```System->Administration->Additional Drivers doesn't list anything.

Can anybody help me? Thanks for any suggestions,
Martin

---

### Post by superduperlinuxperson on 2011-06-12
run this command 
lspci -vnn | grep 14e4

and tell me what the output is
thanks

---

### Post by martin_385 on 2011-06-12
lspci -vnn | grep 14e4
```
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

---

### Post by josephmills on 2011-06-12
download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
``` 
[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ?  If you have any trouble just post

---

### Post by martin_385 on 2011-06-12
works :-)

thanks a lot!

---

### Post by josephmills on 2011-06-12
> **martin_385 said:**
> works :-)

thanks a lot!

please mark as solved have fun

---

### Post by bradtrivers on 2011-06-23
I just wanted to say thank you, thank you, thank you!  I had the same problem with a Gateway laptop I'm running and your instructions worked like a charm!

---

### Post by jrkrideau on 2011-06-26
> **josephmills said:**
> please mark as solved have fun

I have had the same problem and *solved* slightly differently since I had no Ethernet connection available.  [http://ubuntuforums.org/showthread.php?t=1790338](http://ubuntuforums.org/showthread.php?t=1790338) .

I now have reached the router, in fact I seem to be picking up 6-7 local sites. I have authenticated myself with my site but I am unable to actually reach the internet.  The connection is actually working as I can access it from the Windows 7 side of my double boot machine.

I'm an almost complete linux newbie and not much better on wireless accces. Any suggestions that I might try?

Thanks

---

### Post by banjo5150 on 2011-07-04
Thanks this just helped me a lot. I am a complete Linux newb. Worked like a charm.

---

### Post by MaindotC on 2011-07-04
Thread is still not marked as solved...

---

### Post by fawkes12 on 2011-07-06
hello im an ubuntu newbie too , installed ubuntu recently used the ndswrapper to install the driver for my card BUT it keeps saying firm ware missing 
the output of lspci -vnn | grep 14e4:
01:00.0 network controller [0280] broadcom corporation bcm4312 802.11b/g LP-PHY [14e4:4135] (rev 01)

i've tried the charm above but didnt worked for me 
i've tried many things but i always encounter some sort of difficulty
please help!!!

---

### Post by RikiKikiTaco on 2011-07-23
I have the same problem with the same output from lspci -vnn |grep 14e4
If someone knows what I can do please help.

Thanks,
Riki


> **fawkes12 said:**
> hello im an ubuntu newbie too , installed ubuntu recently used the ndswrapper to install the driver for my card BUT it keeps saying firm ware missing 
the output of lspci -vnn | grep 14e4:
01:00.0 network controller [0280] broadcom corporation bcm4312 802.11b/g LP-PHY [14e4:4135] (rev 01)

i've tried the charm above but didnt worked for me 
i've tried many things but i always encounter some sort of difficulty
please help!!!

---

### Post by nm_geo on 2011-07-23
Are you sure the pci # is [14e4:41[COLOR=Red]**35**[/COLOR]]

Please run in terminal and post results:

```
lspci -nn | grep 0280
```

It is best to just copy the command in the box and paste in the terminal. Then hit return.  Copy terminal results and paste here...
I hope Broadcom has not got a new pci with that number.. 
[14e4:4315] we can deal with.

---

### Post by RikiKikiTaco on 2011-07-23
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by nm_geo on 2011-07-23
> **RikiKikiTaco said:**
> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Ok what version of Ubuntu are you running?
```
cat /etc/lsb-release; uname -r
```

We can probably go to Synaptic and install 
b43-fwcutter 
firmware-b43-lpphy-installer

If you have tried the STA (wl) remove 
bcmwl-kernel-source

---

### Post by RikiKikiTaco on 2011-07-23
I am running 11.04 
I tried using the file that was posted at the beginning of this thread but it wasn't working. I followed the instructions as they were posted. I haven't tried the other thing but, I don't know how. I just installed this today. So, I'm as new as new gets. Thanks for helping and understanding.

---

### Post by nm_geo on 2011-07-23
> **RikiKikiTaco said:**
> I am running 11.04 
I tried using the file that was posted at the beginning of this thread but it wasn't working. I followed the instructions as they were posted. I haven't tried the other thing but, I don't know how. I just installed this today. So, I'm as new as new gets. Thanks for helping and understanding.

Let try something simple

Go to Synaptic PacKage Manager
Do a search on _bcm_
you should see 
    b43-fwcutter
    firmware-b43-<<<<< see above
Choose those to install .. and apply

---

### Post by nm_geo on 2011-07-23
You are running Unity Desktop correct?

Just look for Applications in the left hand panel..
Under Installed see move click on that little button
Scroll down to Synaptic (type in password if asked
then search box put in_ bcm_
then select to install
  b43-fwcutter
  firmware-b43-lpphy-installer
Apply
Reboot without ethernet cable attached set up wireless

---

### Post by RikiKikiTaco on 2011-07-26
> **nm_geo said:**
> You are running Unity Desktop correct?

Just look for Applications in the left hand panel..
Under Installed see move click on that little button
Scroll down to Synaptic (type in password if asked
then search box put in_ bcm_
then select to install
  b43-fwcutter
  firmware-b43-lpphy-installer
Apply
Reboot without ethernet cable attached set up wireless

Sorry, I've been away for a couple days. I went to synaptic package manager. Searched "bcm" the only thing that came up was "libklibc"

I have b43-allfw.tar_.gz saved in a folder marked wireless. Because I don't have access to the internet from my laptop, I have to download and transfer all files from my netbook which is running an earlier version of eeebuntu.

---

### Post by ransta73 on 2011-08-10
Works Great! THANKS!!!

---

### Post by oskarishappy on 2011-09-21
I followed all of Josephmills steps and I got an error at "tar -xzf b43-all-fw.tar_.gz". The file is now called "all.tar", and doing "tar -xzf all.tar" did not work. However, I did do "tar -xvf all.tar" and that worked. However, nothing changed after I rebooted. Any help? 

Thank you :)

---

### Post by Riglpo on 2011-09-24
Thank you sincerely josephmills, that also worked for me after many other frustrating approaches ;-)

---

### Post by jda868 on 2011-11-29
When I get to the part of placing the folder in the firmware directory, I type the command in and it prompts me for my password, which will not show; only a flashing white box. Help me please ;)

---

### Post by jda868 on 2011-11-29
It worked. I had something wrong with the folder; renamed the folder and it worked :)

---

### Post by smaxton on 2011-12-03
worked!

---

### Post by smaxton on 2011-12-04
> **nm_geo said:**
> You are running Unity Desktop correct?

Just look for Applications in the left hand panel..
Under Installed see move click on that little button
Scroll down to Synaptic (type in password if asked
then search box put in_ bcm_
then select to install
  b43-fwcutter
  firmware-b43-lpphy-installer
Apply
Reboot without ethernet cable attached set up wireless


thanks heaps this worked for me

---

### Post by jayad08 on 2012-01-07
hats off.. worked instantly..
thanks a ton, was searching for this fix for long..

---

### Post by Spuriousd on 2012-02-04
Thank you much for posting this fix! I was getting discouraged by the process, but your instructions worked like a charm and now I'm deep into my infatuation with Ubuntu.

---

### Post by Luke oX on 2012-05-17
Thank you so much @josephmills!!!

---

### Post by letonice on 2013-05-01
Thank you so much....It worked....!

---

### Post by letonice on 2013-05-01
:popcorn:

---

### Post by rirchse on 2013-05-01
Many many thanks.......[ 						 					]("http://ubuntuforums.org/member.php?u=1238005") 				 				 					 						 	[**[COLOR=#DD4814][B]josephmills**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1238005").

---

### Post by wildmanne39 on 2013-05-01
Thread closed. Please do not post in old threads.

---

