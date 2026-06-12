---
title: "Connected but not online"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by elliotn on 2010-09-02
Help guys
I use bluetooth and my SE W890i to connect to the
net. It has worked well before
but recently mn-applet shows
that I am connected but not even
SYNAPTIC would download
parkages nor Firefox connecting
to pages.
I need to update desperately.

In windows all work fine

---

### Post by Austin25 on 2010-09-02
How are you posting?

---

### Post by 3rdalbum on 2010-09-02
[http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

---

### Post by elliotn on 2010-09-02
> **Austin25 said:**
> How are you posting?
well I dont know what you mean but if you mean how am I posting this thread if i dont have net, then the answer is I am using a cellphone to post here.

---

### Post by K.Mandla on 2010-09-02
Moved to Networking and Wireless.

---

### Post by MaindotC on 2010-09-02
You'll have to follow the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and determine where you are having the issue.  Please let us know at what point you are having difficulty or where you are not receiving the desired output from the commands listed.

---

### Post by elliotn on 2010-09-03
> **3rdalbum said:**
> [http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

Tried that but still wont help

---

### Post by elliotn on 2010-09-03
> **strAlan said:**
> You'll have to follow the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and determine where you are having the issue.  Please let us know at what point you are having difficulty or where you are not receiving the desired output from the commands listed.

I checked the guide but i couldnt find a solution

---

### Post by BkkBonanza on 2010-09-03
You cannot expect useful help here without details of your system and networking config. Post output of **ifconfig**, **route**, and **cat /etc/networking/interfaces** commands for starts. Then we have some idea of how you are configured and may be able to suggest something other than random thoughts.

---

### Post by MaindotC on 2010-09-03
> **BkkBonaza said:**
> You cannot expect useful help here without details of your system and networking config. Post output of **ifconfig**, **route**, and **cat /etc/networking/interfaces** commands for starts. Then we have some idea of how you are configured and may be able to suggest something other than random thoughts.

That kind of output is directed in the wireless troubleshooting guide which is why I post it so frequently.

---

### Post by BkkBonanza on 2010-09-03
@strAlan, yes I know. It's good for him to go through that.
But he's at a dead end and hasn't provided anything for people to help him.

---

### Post by MaindotC on 2010-09-03
> **BkkBonaza said:**
> @strAlan, yes I know. It's good for him to go through that.
But he's at a dead end and hasn't provided anything for people to help him.

Ok np - I just felt that if he went through the guide he would have posted those things if they seemed incorrect.  Perhaps not.

---

### Post by elliotn on 2010-09-05
Here is the requested info

---

### Post by elliotn on 2010-09-05
> **BkkBonaza said:**
> You cannot expect useful help here without details of your system and networking config. Post output of **ifconfig**, **route**, and **cat /etc/networking/interfaces** commands for starts. Then we have some idea of how you are configured and may be able to suggest something other than random thoughts.

Please see the attached .txt file regarding the requested info


Please help.

---

### Post by BkkBonanza on 2010-09-05
Your info indicates you don't have a default route set. This would prevent any internet traffic from reaching your gateway.

Please try this command and report back, show output of route after this,

sudo route add default gw 41.14.113.125

---

### Post by elliotn on 2010-09-05
> **BkkBonaza said:**
> Your info indicates you don't have a default route set. This would prevent any internet traffic from reaching your gateway.

Please try this command and report back, show output of route after this,

sudo route add default gw 41.14.113.125

Well here is another attachement, i got an error when I did the above command.

---

### Post by BkkBonanza on 2010-09-05
Well, your mobile link looks like it was dropped/reconnected because now you have a different IP address. You have a default route set now. So that's good. But I don't know about your other settings, ifconfig and interfaces file. So I can't say whether your default route is correct.

That message you got about "SIOCADDRT: No such process" indicates that the driver is likely having some problem. I don't know much about bluetooth-ethernet interfaces and what driver was installed to handle that. If you went through some steps to install your bluetooth phone/modem then you likely need to redo that.

You're going to need someone who is more familiar with how that bluetooth interface works.

---

### Post by elliotn on 2010-09-05
> **BkkBonaza said:**
> Well, your mobile link looks like it was dropped/reconnected because now you have a different IP address. You have a default route set now. So that's good. But I don't know about your other settings, ifconfig and interfaces file. So I can't say whether your default route is correct.

That message you got about "SIOCADDRT: No such process" indicates that the driver is likely having some problem. I don't know much about bluetooth-ethernet interfaces and what driver was installed to handle that. If you went through some steps to install your bluetooth phone/modem then you likely need to redo that.

You're going to need someone who is more familiar with how that bluetooth interface works.

Thanks man for your help, the bluetooth driver is the default one that comes with ubuntu, I never installed anything

---

### Post by MaindotC on 2010-09-05
Was this link working fine and then it stopped working?

---

### Post by elliotn on 2010-09-05
> **strAlan said:**
> Was this link working fine and then it stopped working?

Which link?

---

### Post by BkkBonanza on 2010-09-05
I looked up that "SIOCADDRT: No such process" error. Apparently it's caused when the IP address given is not part of your network and it can't find the device to assign it to. I'm guessing this is because when you did the command the phone had already re-connected with a new IP.

There is some misconfiguration in your network settings. If you haven't already tried it then definately try restarting networking. 

sudo /etc/init.d/networking restart

Every time the bluetooth connection drops/reconnects you're going to get a new IP. There usually would be DHCP handling that, using dhclient3, but I just don't know enough about how your phone, ISP and bluetoooth all interact.

strAlan is asking about your "bluetooth internet link" and whether it was working before. Something must have changed in the config.

---

### Post by elliotn on 2010-09-05
> 
strAlan is asking about your "bluetooth internet link" and whether it was working before. Something must have changed in the config.

Yes it worked perfect before. This just started to happen recently.

---

### Post by MaindotC on 2010-09-05
Sorry, when I said link I mean link to the network, or in this case link to the internet.  What happened prior to it not working?

---

### Post by elliotn on 2010-09-06
> **strAlan said:**
> Sorry, when I said link I mean link to the network, or in this case link to the internet.  What happened prior to it not working?

It was linked to the internet, it just stopped working, I wanted to download mp3info via Synaptic but it wouldnt download, so I tried firefox but it wouldnt load pages either

---

### Post by MaindotC on 2010-09-07
Well I can't really provide good assistance for you because I don't have a lot of experience using IP over bluetooth.  However I'll keep trying.  At what point when using the wireless troubleshooting guide were you unable to proceed?  I know it's not a guide meant for IP over BT, but it does run you through general network troubleshooting steps that apply to any IP network.

---

### Post by elliotn on 2010-09-07
well mate thanks for all the help, I think it will be better if I backup my system and reinstall, coz I seen not to come with a solution, But first will try to update with keryx and see if the problem still persist, if it does then I will reinstall.

---

### Post by MaindotC on 2010-09-07
May I advise against re-installing - is not really solution.  I realize it may take less time but you should get away from that because that's typically how Windows machines are "fixed".  The issue you're dealing with is very small - probably a configuration file - even though it's very difficult to find.  I was googling and I found [this link](http://bluez.sourceforge.net/contrib/HOWTO-PAN) which talks about a package you can install to enable IP over BT.  I really didn't want to ask you to install another application because as you said it was working earlier and thus it wouldn't make sense for you to install something new.  However, it may save you a re-install.

Also, I wondered - is there some reason you can't just use a wifi card?  Don't you have one in your machine?

---

### Post by elliotn on 2010-09-08
I dont have the wifi card in my pc, i will look at the link, the page look weird though.

Maybe i should remove the bluetooth parkages and reinstall them and see if it help

---

### Post by MaindotC on 2010-09-08
If you do make sure you use the --purge command so it will remove any configuration files as well, or use Synaptic and click "completely remove" for each package.

---

### Post by elliotn on 2010-09-09
I removed bluez and reinstalled it but i cant find the bluetooth applet now.

Just connected with usb cable and it works, I am able to go online. And my system is up to date

---

### Post by MaindotC on 2010-09-09
Well you may want to try installing that bluetooth package or searching for other IP over bluetooth solutions.  Also, I neglected to consider that if your machine was connected to your phone, which is acting as a gateway to the Internet, and all of a sudden it isn't working then perhaps there was a configuration changed in your phone.

---

### Post by elliotn on 2010-09-09
> **strAlan said:**
> Well you may want to try installing that bluetooth package or searching for other IP over bluetooth solutions.  Also, I neglected to consider that if your machine was connected to your phone, which is acting as a gateway to the Internet, and all of a sudden it isn't working then perhaps there was a configuration changed in your phone.

well for now my problem is solved as i got a Htc hero to use as modem and all is working fine.

---

