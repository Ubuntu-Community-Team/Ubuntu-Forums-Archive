---
title: "mtn broadband connection 9.04"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by 10ghost on 2010-03-12
Hi readers,
I attempted using the MTN broadband usb on a 9.04 but discovered that it recognised the GSM providers . On selection of MTN on network applet option it connected but i Could not browse .
I do not know what exactly could be the problem or how can i troubleshoot it to help give proper details so as to help me in resolving this problem.
I also tried the Glo broadband it did not also work.

---

### Post by alexfish on 2010-03-12
Hi


 There are possibly three ways do this
 

 1:
 Thread by Silvertones   Post # 1
 [http://ubuntuforums.org/showthread.php?t=1426409](http://ubuntuforums.org/showthread.php?t=1426409)
 
Code:
gksudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute
 

 try the above first
 

 2:
 Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30 ( or any thing above the default value till there is a constant connection )

Code:

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30

Hopefully I can now leave the NM IPv4 settings to Automatic (PPP) instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.


remember if you need to reverse any changes in the options file then Place the # back in front of the entry IE  # ipcp-max-failure 30

[http://ubuntuforums.org/showthread.php?t=1331660&page=3](http://ubuntuforums.org/showthread.php?t=1331660&page=3)
 Post # 23
 

 3:
 Setting the NM to IPv4 settings to Automatic (PPP) address
 

 On the Ubuntu system there should be two files “serviceproviders.2.dtd” and “serviceproviders.xml”
 

 below is a part sample from the file
 

 

 <username>mnet</username>
 <password>mnet</password>
 <dns>[COLOR=#2323dc]194.170.1.6[/COLOR]</dns>    <----------- This one
 <dns>[COLOR=#2323dc]194.170.1.7[/COLOR]</dns>    <------------and this one
 </apn>


or contact your service privider

 

 look up your ISP and Payplan from this file then locate the two addresses like the ones highlighted in blue ,set the NM to IPv4 settings to Automatic (PPP) address  enter the numerical addresses in the  DNS servers box . 



Example    194.170.1.6 , 194.170.1.7
 

 Try them all and see what happens,  
 

 if they work let us know which in your mind is the best solution to the problem

---

### Post by thedandalion on 2010-03-12
I am very new to Ubuntu and linux.  I have put it on my laptop and it works beautifully and wish I did this sooner.  I put it on my desktop and have found that I can connect to the net but not browse.  I see the fixes on here but being as new as I am I do not know exactly where to enter the codes and such.  Can someone help me?

Thanks a bunch :D

---

### Post by alexfish on 2010-03-13
> **thedandalion said:**
> I am very new to Ubuntu and linux.  I have put it on my laptop and it works beautifully and wish I did this sooner.  I put it on my desktop and have found that I can connect to the net but not browse.  I see the fixes on here but being as new as I am I do not know exactly where to enter the codes and such.  Can someone help me?

Thanks a bunch :D

                                 Hi
 

 for the terminal etc
 

 follow the screen shots below  
 

 Note when editing files it is wise to make a backup of the original file "wise if your are a novice but also good practice"

 

 eg open the file with gedit, then from the menu save as “filename”_bak”
 


 then go to the original file ,or mark any changes as shown in the screen shot
 
For network manager you should see a tabbed window " click on the tabs page "


regards

alexfish

---

### Post by thedandalion on 2010-03-14
Thank you.... I tried these and it didnt work... :( you have any other suggestions?

---

### Post by alexfish on 2010-03-14
> **thedandalion said:**
> Thank you.... I tried these and it didnt work... :( you have any other suggestions?

HI
are you using the network manger for the connection

if not which method are you using to connect

also could you post details of this output of the following commands from the terminal

Code:

dmesg | grep -e "modem" -e "tty"

from a second terminal

Code:

tail -f /var/log/syslog

---

### Post by thedandalion on 2010-03-15
Yes, I am using the network manager

This is what I got when when I typed in the first code

[    0.002036] console [tty0] enabled

the tty is in red

---

### Post by alexfish on 2010-03-15
> **thedandalion said:**
> Yes, I am using the network manager

This is what I got when when I typed in the first code

[    0.002036] console [tty0] enabled

the tty is in red

Hi again

I think we will have to take this step by step so please be patient

This the output of the command with no modem attached ; please note the modem i am using is different to yours so your outputs may vary 

dmesg | grep -e "modem" -e "tty

[    0.001934] console [tty0] enabled
[    0.771123] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.771364] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


This is the output of the command after modem is attached a device which shows up on the desktop which I eject "right click on the icon for menus"

 dmesg | grep -e "modem" -e "tty"

[    0.001934] console [tty0] enabled
[    0.771123] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.771364] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  156.131618] USB Serial support registered for GSM modem (1-port)
[  156.131685] option 1-4:1.0: GSM modem (1-port) converter detected
[  156.131801] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0
[  156.131832] option 1-4:1.1: GSM modem (1-port) converter detected
[  156.131913] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1
[  156.131952] option 1-4:1.3: GSM modem (1-port) converter detected
[  156.132092] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2
[  156.132120] option: v0.7.2:USB Driver for GSM modems

Do you have similar outputs



I have used the copy and paste function from the mouse menus to post this from the terminal to the Ubuntu reply text area , try to do the same

 Regards alexfish

---

### Post by thedandalion on 2010-03-15
I know its gonna take some time... with me being a newb and all :D  I am just thankful that you are taking the time to help me work this out.

When I ran the code the first time I didnt have it plugged in.  I am on my laptop now and have to move my wireless stick back and forth

so with the stick in and active this is what it said

[ 0.002039] console [tty0] enabled
[62.754904] cdc_acm 4- 3:1.0: ttyACMO: USB ACM device
[62.759479] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems a
nd ISDN adapters

---

### Post by alexfish on 2010-03-16
When you plug the device in does any icon appear on the desktop , also does a "make new connection" appear in the network manager menus. NM is located on the right of the top menu panel. if a device shows on the desktop and nothing shows in the network manager, try ejecting the device, then check NM again

---

### Post by thedandalion on 2010-03-16
> **alexfish said:**
> When you plug the device in does any icon appear on the desktop , also does a "make new connection" appear in the network manager menus. NM is located on the right of the top menu panel. if a device shows on the desktop and nothing shows in the network manager, try ejecting the device, then check NM again

When I plug it in no icon shows up but when I click on the 'tower' it shows it active and ready to connect.  When I very first set it up I went through the network connections and it prompted me to connect it and put in the correct information.  When I plug it in and out it doesnt show it on the desktop, just shows it in the pop down menu when I click on the 'tower'

---

### Post by alexfish on 2010-03-16
Ok

 from the network manager if it shows available connection then click on the connection
does the little wheel spin and then stop after a while, then does the network manager show the connection has been made. if so  right click on NM , then click on Connection information and post and information shown

regards

alexfish

---

### Post by thedandalion on 2010-03-16
> **alexfish said:**
> Ok

 from the network manager if it shows available connection then click on the connection
does the little wheel spin and then stop after a while, then does the network manager show the connection has been made. if so  right click on NM , then click on Connection information and post and information shown

regards

alexfish

Yes it lets me connect (screen shot showing connection) it will let me browse about two pages before it seizes up on me.  "Connection Information" doesnt seem to exist on mine.  When I click on the icon it gives me a pop down menu. and shows that it is connected, it gives me an option to disconnect.  For some reason I can not get a screen shot of it. ggrrr... 

[ATTACH]150319[/ATTACH]

---

### Post by alexfish on 2010-03-17
Hi

try right click on the NM for 2nd menu list ,then select connection information take a note of the info then post details of

ip address
broadcast address
submask
default route
primary address
secondary address

---

### Post by thedandalion on 2010-03-19
> **alexfish said:**
> Hi

try right click on the NM for 2nd menu list ,then select connection information take a note of the info then post details of

ip address
broadcast address
submask
default route
primary address
secondary address

Sorry it took me so long to get back to you.  My work schedule changed and I havent had a lot of time for my puters :D

I have a screen shot of the info you need

[ATTACH]150657[/ATTACH]

Thanks :D

---

### Post by alexfish on 2010-03-20
hi

looking at the screen shot all the connections have been made so the browser should work

if not check the network settings in the browser.  on firefox click Edit /Preference this will open a window. Select Network then settings. with mobile broadband the connection setting can be set at No Proxy and should work ok,also check the the browser is set to work on line.

from the connection information make a note of the primary and secondary address,this is helpful if the NM finds it difficult to make the connections,this is not a fault of NM but a combination of the modem firmware and your ISP, if the ISP fails to provide the correct configuration info before the time out period then only the default route will be returned.Hence the usual Thread Headed by My Modem Is Connecting But the browser don't work.

So  If this happens one cure is to set the IPv4 to Automatic (PPP) address only . in your case enter  " 172.28.221.53 , 172.28.221.54  " in the DNS Servers Text Box.

Or you can try others as mentioned in the previous posts.Assuming the correct info has been entered in the NM and the primary and secondary address is not been resolved at any stage .

Let us know if the browser is working

regards

alexfish

---

### Post by thedandalion on 2010-03-21
Thank you so much... I tried both suggestions but it didnt fix it... I am going to check out the thread you suggested and see if there is other things I can do.  Its very frustrating because it lets me jump about two pages before it seizes up on me... ggrrr..

---

### Post by alexfish on 2010-03-21
hi

sorry to here about the browser problem

but lets check if the system will update first 

from the terminal try this code

Code:

sudo apt-get update

if this works then we will try to see if the problem is with the browser

also assuming the update works you may want to install pppstatus via synaptic, this is a monitor for the ppp, run pppstatus from the terminal

Code:

pppstatus

regards

alexfish

---

### Post by thedandalion on 2010-03-21
Ok, I connected to the net and typed in the code for updates and this is what I got..
[ATTACH]150911[/ATTACH]
It stayed like this for a bit... I left the puter and came back about 15 minutes later and this is what I got...
[ATTACH]150912[/ATTACH]
It continued for a bit and this is the end...
[ATTACH]150913[/ATTACH]

My update manager popped up but I couldn't update because of the net not working.  It makes me think that its not the browser but my connection of some kind.  It connects stays active for less than a minute then freezes up....

---

### Post by alexfish on 2010-03-22
hi

not sure what is happening here

none of the returned addresses you have ping from my system,yet the address shown in the above screen shot does, try deleting the existing connection in the NM and reconfigure the device with NM, ensure the correct info is entered if in doubt ask your service provider, also disable and other network connections Like a wired and wireless.

can you post the details you have entered in the network manager


have you altered any other settings with the networking/ manager or configuration files

regards

alexfish

---

### Post by thedandalion on 2010-03-24
The only alterations that I have made are the ones that we went through in the thread.  While looking around and messing with a bit I managed to delete the Icon from the toolbar and now do not seem to have a way to connect.  I played around looking for it and trying to put it back but only managed to find a pretty cool fish and some eyes.  How do I get it back?

---

### Post by alexfish on 2010-03-24
> **thedandalion said:**
> The only alterations that I have made are the ones that we went through in the thread.  While looking around and messing with a bit I managed to delete the Icon from the toolbar and now do not seem to have a way to connect.  I played around looking for it and trying to put it back but only managed to find a pretty cool fish and some eyes.  How do I get it back?

in the top right panel right click with mouse / select add to panel , then select  "notification area" I think , you may have to reboot to  see NM again

regards

alexfish

---

### Post by thedandalion on 2010-03-29
Woot! got it back... :D

Ok here are screen shots of the information of my connection. I have been floating around the forum looking at other posts about connecting and freezing up and none of them seem to 'fit' to help fix my problem.
[ATTACH]151777[/ATTACH][ATTACH]151778[/ATTACH][ATTACH]151779[/ATTACH]

---

### Post by alexfish on 2010-03-29
Hi

can you provide some info

1. confirm that your ISP is MTN

2. Your Country

3. your pay plan If any

4. do you have a pin code activated



from this I may be able to find the correct settings for the network manager

---

### Post by thedandalion on 2010-03-29
MTN?  I am not sure what that is...

It works on my laptop and its set up the same way.  When I first set it up it asked for country (USA) and then carrier (Cricket) then it takes me to the network manager so I can put in my number.

---

### Post by alexfish on 2010-03-29
Hi

Now we Know you are on cricket

you could try these threads

[http://ubuntuforums.org/showthread.php?t=928957&highlight=cricket](http://ubuntuforums.org/showthread.php?t=928957&highlight=cricket)

[http://ubuntuforums.org/showthread.php?t=1146110&highlight=cricket](http://ubuntuforums.org/showthread.php?t=1146110&highlight=cricket)

regards

alexfish

---

