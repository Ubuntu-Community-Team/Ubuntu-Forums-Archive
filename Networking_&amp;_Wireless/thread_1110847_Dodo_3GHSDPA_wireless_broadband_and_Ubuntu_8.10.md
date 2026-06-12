---
title: "Dodo 3G/HSDPA wireless broadband and Ubuntu 8.10"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by cam987 on 2009-03-30
Hi,

I have just upgraded to Ubuntu 8.10 and the only internet access I have is a Dodo 3G/HSDPA USB modem (Huawei E169).

The first time I put the modem in, the Network Manager opened and I followed the instructions and set up an Optus wireless broadband connection (Dodo uses the Optus network) as Dodo was not in the list of service providers.  When I try to connect it disconnects me straight away.  

I have searched through these forums and tried to fix as per the Virgin Broadband, OPtus, but no matter what values I put in the Network Manager, it still disconnects me straight away.  I have also tried putting in my Dodo username and password in the Network Manager, but then it just prompts me for a password, and then disconnects.

The standard Optus setup I have tried uses these values,

Optus Australia APN Settings
Here are the APN settings that you will need to get online. 
APN: internet
Username: {blank}
Password: {blank}
DNS: 202.139.83.3, 192.65.91.129

I have also tried modifying the /etc/ppp/options file as per the post [SOLVED] Huawei e169 USB modem - Virgin Broadband - Australia [solved] as this person was having similar issues, but that didn't work.

Has anyone else got the Dodo wireless modem working?

Could it be something to do with Dodo using Optus?  The instructions (for Win and Mac) that come with the modem both require Dodo's SP code 335D1 to be entered during setup.  I have a dual partition and when I use the modem in windows, it connects as 335D1, not my username and password.  Do I need to enter this Dodo SP code in the Network Manager?  If yes, where?

Any help would be greatly appreciated!

Thanks,
Laura

---

### Post by thewolfman on 2009-03-30
Hi Laura,

try going into a terminal and type: sudo pppoeconf then type your password and follow the rest like its written, it should get you online.

Regards Stephen.

---

### Post by cam987 on 2009-03-30
Thank you, I'll try that.

Laura

---

### Post by shetlandpony on 2009-04-05
Hello Laura,

I am using the Optus wireless network in a similar way to you.

I have Optus wireless broadband (Huawei E169) rebundled via my local ISP.

To get it up and running all I had to do was the following.

1. If you can get your Windows connection settings via Network Centre for the Huawei modem (in Network Centre it is something like - choose  "Connections" then "Properties" etc). Get your APN, DNS settings and the Authentication code/number. Write them down (You may not need anything other than the APN, if the auto-detection has worked in 8.10).

2. Shut down and boot into 8.10.

3. Open Network Manager. Select the "Mobile Broadband" tab.
   The fields should be as follows:
    - Under "Basic" in the "Number" field enter the "Authentication" setting you wrote down for Windows eg. *99#. Leave the other fields blank.
    - Under "Advanced" and "APN" enter your APN that you got from Windows. Leave all other fields and boxes blank or unticked.

4. Leave the next tab - "Point-to-Point Protocol (PPP)" - as it is.

5. Go to the "IPv4 Settings" tab. Ensure that the "Method:" field is set to "Automatic (PPP) addresses only". You may not need to do anything else. Just click "OK" and exit and then try to connect. However, you can add your DNS addresses you recorded from Windows in the "DNS Servers" field in the format xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx (this probably isn't necessary, but I have mine in there). Save and try to connect. No browser configuration required.

This worked for me. The first time I connected to the Optus network, but kept timing out in Mozilla. But this was just the connection being so poor. The second time I tried it it worked fine. I'm updating the packages as I type now.

Hope this helped.


Shetlandpony (Rod)

---

### Post by cam987 on 2009-04-10
It dawned on me a couple of days ago to get the settings from the windows connection!

For a Dodo wireless modem I did the following,

Open the Network Manager
Create a new Optus 3G wireless connection 
Edit the connection and change the APN to dodolns1 (I didn't have to change anything else, the Optus 3G settings are correct)
Connect to the internet

I appreciate everyone's help, thank you very much :)

Regards,
Laura

---

### Post by Master Darko on 2009-05-12
This is what i had to do in order to get Dodo wireless internet to work.

1. Add 'Optus 3G' mobile broadband connection under Network Connections.
2. Edit it.
3. Change APN to dodolns1 (Mobile Broadband tab)
4. Change DNS Servers to 202.136.43.197, 202.136.42.229 (IPv4 Settings tab)
5. Connect and enjoy the internet!

PS. If you dont change the DNS servers, it still connects but fails to open any page.

---

### Post by rikb on 2009-05-16
> **shetlandpony said:**
> Hello Laura,

I am using the Optus wireless network in a similar way to you.

I have Optus wireless broadband (Huawei E169) rebundled via my local ISP.

To get it up and running all I had to do was the following.

1. If you can get your Windows connection settings via Network Centre for the Huawei modem (in Network Centre it is something like - choose  "Connections" then "Properties" etc). Get your APN, DNS settings and the Authentication code/number. Write them down (You may not need anything other than the APN, if the auto-detection has worked in 8.10).

2. Shut down and boot into 8.10.

3. Open Network Manager. Select the "Mobile Broadband" tab.
   The fields should be as follows:
    - Under "Basic" in the "Number" field enter the "Authentication" setting you wrote down for Windows eg. *99#. Leave the other fields blank.
    - Under "Advanced" and "APN" enter your APN that you got from Windows. Leave all other fields and boxes blank or unticked.

4. Leave the next tab - "Point-to-Point Protocol (PPP)" - as it is.

5. Go to the "IPv4 Settings" tab. Ensure that the "Method:" field is set to "Automatic (PPP) addresses only". You may not need to do anything else. Just click "OK" and exit and then try to connect. However, you can add your DNS addresses you recorded from Windows in the "DNS Servers" field in the format xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx (this probably isn't necessary, but I have mine in there). Save and try to connect. No browser configuration required.

This worked for me. The first time I connected to the Optus network, but kept timing out in Mozilla. But this was just the connection being so poor. The second time I tried it it worked fine. I'm updating the packages as I type now.

Hope this helped.


Shetlandpony (Rod)

these instructions worked perfect for me to get my optus 3g dongle connected in the network manager of my laptop [toshiba portege]. however i found that even though it said i was connected i was unable to load any pages or do any internet related things [synaptic etc]. after forum trawling for days i found some other people with similar problems who had discovered that they could load pages if they typed in ip addresses which i found was also the case for me. The solution for this problem was to Go to the "IPv4 Settings" tab and change the method field from "Automatic (PPP) addresses only" to "Automatic (PPP)"
 which was in contradiction to your instructions in step 5 but it fixed the problem straight away and gave me sweet, sweet unencumbered internet joy. however to get the dongle working on my home computer it needed to be set as per your instructions. i started to wonder why but then i just decided to accept it and enjoy the internet.

---

### Post by Stealth1956 on 2009-05-25
Hi.
I am useing an Option GT Max 3.6 pcmcia card (3G HSDPA etc). This works very well in many parts of the world with a local sim card. I have in the past used an Optus pre-paid sim but due to a change of computer lost the APN, Username and password details for a pre-paid service. Any help on these three details or sugestions of an alternative provider to use in the Sydney area would be most appreciated.
 
CD

---

### Post by M3TA4 on 2011-01-15
I have ubuntu 10.10 

and have been looking around in google for a bit. And found no settings, tuts or manuals for my al300. Except for this one 

[http://forums.whirlpool.net.au/archive/1591671](http://forums.whirlpool.net.au/archive/1591671)

but that didnt work. So I figured it could be a few things. Kernel and/or ubuntu version and/or dodo dongle AL300 model. So what I did and totally got LUCKY on. Was to swap the sim card into another mobile dongle.. Which was a HUAWEI Mobile Model:E160E and it worked. With the setting I used in the link above. I am guessing that optus didnt cap that model or something?

But anyways, That was how I did it. Thought I note it, just incase needed later.

BTW I am on my laptop specs.

---

