---
title: "Re:  Option iCON 515m wireless USB modem (Orange)"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by alexfish on 2009-12-10
[SIZE=2]**Please Checkout Post** [/SIZE]#[**17**]("http://ubuntuforums.org/showpost.php?p=8969792&postcount=17")[SIZE=2] by **Pharscape first** { this line added } Mon 15 MAR 2010

This is a small update to HSOconnect that allows it to work with the iCon 515 as sold by Orange. (5x5[/SIZE] series) so may work with others

**Note:**
**if the ozerocdoff fails to switch the device ,try usb_modeswitch**

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

**READ first , also it may be necessary to un-install ozerocdoff  (ozerocdoff is based on usb_modeswitch)**

**Some Releases of Ubuntu have HSO link in the synaptic package manager /  check it out**


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Link to Debian PKG

                                 [http://www.pharscape.org/forum/index.php/topic,847.0.html](http://www.pharscape.org/forum/index.php/topic,847.0.html)
 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[SIZE=2][COLOR=Red]If You Are A Novice Please Seek Help [/COLOR][/SIZE]

Install the ozerocdoff utility:          

                          [http://www.pharscape.org/ozerocdoff.html](http://www.pharscape.org/ozerocdoff.html)
 
1. Download the udev-icon5x5-pharscape-091208.tar.gz,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,[[IMG]http://pharscape.org/forum/Themes/pharscape/images/icons/clip.gif[/IMG] udev-icon5x5-pharscape-091208.tar.gz]("http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=39") (25.54 KB - downloaded 3 times.)                                                                   __________________

2. Untar the file:  tar zxf udev-icon5x5*
3. Change to the udev directory: cd udev*
4. Install the udev rules: sudo make install
5. Reboot (to reload the rules!)

Install hsolinkcontrol: [http://www.pharscape.org/hsolinkcontrol.html](http://www.pharscape.org/hsolinkcontrol.html)

 

Install hsoconnect:
1. Download the hsoconnect-1.2.19.tar.gz file
2. Untar the file : tar zxf hsoconnect*,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,[[IMG]http://pharscape.org/forum/Themes/pharscape/images/icons/clip.gif[/IMG] hsoconnect-1.2.19.tar.gz]("http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=38") (92.92 KB - downloaded 5 times.)
3. Change to the hsoconnect directory : cd hsoconnect*
4. Install hsoconnect : sudo make install




>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

[SIZE=3][COLOR=Navy]Next Step[/COLOR][/SIZE]

 From The Terminal  find the device ID's

Code:

lsusb

Open the file with  

  Code:

 [SIZE=2][COLOR=Navy]sudo gedit /etc/udev/rules.d/51-hso-udev.rules 
[/COLOR][/SIZE] 
 you need to paste two lines of code in different sections.

First line to paste in the ATTRS section:

  Code:

Edit id's According to product  515 = d157  { Should have called this device Icon d517 :  Why can't Manufacturers or Providers put a Label on the Devices LINUX REF Like" { 0af0}:{d517} :{00}":Simple that one

 [SIZE=2][COLOR=Navy]ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}" [/COLOR][/SIZE]

Second line to paste in the SUBSYSTEM section:

  Code:

 [SIZE=2][COLOR=Navy]SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d055", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}" [/COLOR][/SIZE]

Save the file and exit gedit.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


[COLOR=Navy] **Enter your APN **[/COLOR]

Use the Profile / Edit Connection menu. All network providers have different APN's  [Find out From your Provider]

[SIZE=2]This May Help[/SIZE]
                                                                                                                                                                          [ [IMG]http://ubuntuforums.org/images/misc/paperclip.gif[/IMG]]("http://ubuntuforums.org/search.php?searchid=68356762#")                                                                                                                                                      [COLOR=#980101]**[ubuntu]**[/COLOR]                          [Mobile Broadband  can't connect]("http://ubuntuforums.org/showthread.php?t=1331317")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331317") [2]("http://ubuntuforums.org/showthread.php?t=1331317&page=2"))         

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Make Sure All Wireless connections Are Disable

To Use It

 [SIZE=2][COLOR=Navy]Run HSOconnect from the Applications/Internet menu[/COLOR][/SIZE]

 
[SIZE=2][COLOR=Red]
[COLOR=Black][SIZE=1]
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[/SIZE][/COLOR] added ref for Ubuntu 8.10

[http://www.pharscape.org/hso.html](http://www.pharscape.org/hso.html)

[/COLOR][/SIZE]

---

### Post by alexfish on 2009-12-20
[SIZE=2]**[B][FONT=Verdana, Arial][COLOR=#000080][COLOR=Red][Orange]("http://www.filesaveas.com/orange.html")            [/COLOR]GPRS WAP settings:[/COLOR][/FONT]**[/B][/SIZE]

[SIZE=3][COLOR=Black]UK[/COLOR][/SIZE][COLOR=Black] But May Help With Others[/COLOR]

                                               [B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]Orange                  GPRS settings (WAP):
                
                Homepage: [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]http://orange.multimedia/[B]
                Access Point (Contract): [/B]orangewap[/COLOR][/SIZE][/FONT][B]
                [FONT=Verdana, Arial][SIZE=2][COLOR=#000080] Access Point (PAYG): [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]paygwap[/COLOR][/SIZE][/FONT][B]

                  [FONT=Verdana, Arial][SIZE=2][COLOR=#000080]                  Gateway (IP) address : [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]192.168.071.35[B]
                Username: [/B]Orange[B] 
                Password: [/B]Multimedia[B]
                Session type: [/B]Continuous                  / permanent[/COLOR][/SIZE][/FONT][B][FONT=Verdana, Arial]
                [SIZE=2]Authentication: [/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2]Normal
                [/SIZE][/FONT]**[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]              Port number: [/COLOR][/SIZE][/FONT]**[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]9201[/COLOR][/SIZE][/FONT] [FONT=Verdana, Arial][SIZE=2](or 8080)[/SIZE][/FONT]

                                       [B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]Orange                  GPRS settings (Email/Web):                 
                Homepage: [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]http://orange.multimedia/[B]
                Access Point: [/B]orangeinternet[B]
                Access Point (Old PAYG): [/B]payginternet[B] 
                Username: [/B]user[B]
                Password: [/B]pass[/COLOR][/SIZE][/FONT][B][FONT=Verdana, Arial]
                [SIZE=2]Authentication: [/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2]Normal[/SIZE][/FONT][B][FONT=Verdana, Arial]

                [SIZE=2][COLOR=#000080]Email SMTP server: [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]smtp.orange.net[B]
                Prim. DNS Server: [/B]158.043.192.001
                **Sec. DNS Server: **158.043.128.001[/COLOR][/SIZE][/FONT]

---

### Post by cylinderz on 2010-01-19
Thank you very much for your posting. I am always amazed by the generosity of members sharing such useful information so freely. 

I'm trying to get an Orange Icon 515M working with my laptops. I am an ubuntu 8.10 user at the moment. (reluctant to upgrade to 9.10 because I'm running on 3 machines and don't have that much time) 

Your guide has gotten me so so close to success I believe, but something is still missing. 
I have compiled everything successfully and I have also carefully edited the 51-hso-udev.rules file as per the instructions. I had a slight blip when I forgot to set permissions on the HSOlinkcontrol program. Other than that things appear to have gone smoothly. 

I have the HSOconnect1.2 program running and no error messages.
The light on my dongle is flashing but the connect button on HSOconnect1.2 is greyed out. 

Have you any idea what I might still be missing? (the dongle has been checked on a windows machine and seems to work perfectly)  

Many thanks

---

### Post by alexfish on 2010-01-19
> **cylinderz said:**
> Thank you very much for your posting. I am always amazed by the generosity of members sharing such useful information so freely. 

I'm trying to get an Orange Icon 515M working with my laptops. I am an ubuntu 8.10 user at the moment. (reluctant to upgrade to 9.10 because I'm running on 3 machines and don't have that much time) 

Your guide has gotten me so so close to success I believe, but something is still missing. 
I have compiled everything successfully and I have also carefully edited the 51-hso-udev.rules file as per the instructions. I had a slight blip when I forgot to set permissions on the HSOlinkcontrol program. Other than that things appear to have gone smoothly. 

I have the HSOconnect1.2 program running and no error messages.
The light on my dongle is flashing but the connect button on HSOconnect1.2 is greyed out. 

Have you any idea what I might still be missing? (the dongle has been checked on a windows machine and seems to work perfectly)  

Many thanks

Hi 

I have searched the Internet with "error HSOconnect 1.2 is greyed out. Orange"

it has come up wth this , hope it will help

**[PHARscape | AT&T Quicksilver]("http://peck.org.uk/Quicksilver.html?d=")** click

The *hsoconnect* tool opens, but the connect button stays *grayed out* and the unknown scanning never displays **...** *HSOconnect 1.2*.19 for *Orange* iCon515 support **...**
peck.org.uk/Quicksilver.html?d= - [Cached]("http://209.85.229.132/search?q=cache:04j9H97R1_sJ:peck.org.uk/Quicksilver.html%3Fd%3D+HSOconnect+1.2+is+greyed+out.+Orange&cd=4&hl=en&ct=clnk&gl=uk")

I don't know if is relevant , But the site is certainly worth a visit if you have problems

with the HSO connect

There is also a forum here

[http://www.pharscape.org/forum/index.php](http://www.pharscape.org/forum/index.php)

---

### Post by cylinderz on 2010-01-19
Many thanks for such a prompt reply. 

I'm still having no luck (me being somewhat clueless doesn't help I'm sure) 

I believe I have made some interesting progress though
When plugged in go to console and used the command 
lsusb -v | grep Option 

I get 

Bus 005 Device 009: ID 0af0:d157 Option 
  idVendor           0x0af0 Option

I was expecting to see d055 but here was a d157. 
So instead of the d055 suggested  I added these lines :- 

ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d157", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

and 

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d157", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

Hopefully this may be of interest to someone else.

Still no luck though. Connect button still grayed out. 

On the pharscape site (pharscape.org) and related to a similar problem (greyed out connect button) I found this reference: 
It read:

"download and unpack the latest udev tarball from this site, and cd into the udev directory. Then assuming you still have all the required libraries loaded, a simple "make clean && make && sudo make install" will fix the problem."

I used the search box at the top of the pharscape site to look for both udev and tarball but found nothing. Do  you happen to know to what this refers? 

It might be all I need to get this thing going!

---

### Post by alexfish on 2010-01-19
hi

have you checked the user and password are correct

also try a reboot

Also could you look here / keep you id's the same as above

 post #[**6**]("http://ubuntuforums.org/showpost.php?p=8533114&postcount=6")
[http://ubuntuforums.org/showthread.php?t=1356934&highlight=hso+connect](http://ubuntuforums.org/showthread.php?t=1356934&highlight=hso+connect)

---

### Post by cylinderz on 2010-01-21
Every attempt to get this dongle working with ubuntu 8.10 failed. Maybe it does, but I couldn't get it to work no matter how hard I tried.
In the end I bit the bullet and upgraded from ubuntu 8.10 to 9.10 (fresh install)
- SUCCESS!
I can therefore confirm that this dongle (icon 515m) will work quite happily on the asus eee pc running a bog standard installation of ubuntu 9.10 as long as the additional instructions mentioned above are undertaken and worked through carefully a step at a time.

In my case there were some differences though and these appear to relate to the dongle itself. 
re the 51-hso-udev.rules file d505 was not applicable but d157 was. On my icon 515m dongle I needed to add the following lines to the /etc/udev/rules.d/51-hso-udev.rules file

ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d157", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d157", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"

My orange dongle also required a different APN from the one above
I had to use the following:

APN: consumerbroadband
Username: user
Password: pass

All in all this proved to be quite a difficult exercise because I'm a still a bit of a novice when it comes to some of the more complex aspects of using linux. Persistence has paid off though. Many many thanks for all the help.


[ nb THERE WERE SOME SUBSEQUENT PROBLEMS SO YOU NEED TO READ ON AND FIND THE ENTRY REGARDING RESOLVCONF WHICH FINALLY SORTED EVERYTHING OUT]

---

### Post by pdc on 2010-01-21
well done cylinderz;

you did very well to get all that done, and good to know that the install of 9.10 worked well

what does 

> uname -r

give you, from a terminal?

---

### Post by cylinderz on 2010-01-24
It gives me  2.6.31-14-generic

But! early success has proven to be mixed. 
At times this works great and at other times it doesn't no matter what I do. 
I have tried in locations with  strong signal and it makes no difference.  

I am trying to establish a pattern but have so far been unable to. 
Though hsoconnect says i'm connected it's as though I have no network connection. Then at other times it works fine.  
There seems to be no clue in the diagnotic log either hsoconnect says I'm connected but if it doesn't want to play ball..... nothing. 

Dongle tested again in windows - works fine. Very frustrating. I am wondering about trying a different dongle 

Does anyone know if there are any orange dongles which are known to work consistently  well with ubuntu? 

Many thanks

---

### Post by alexfish on 2010-01-24
hi

could you post the last 15 lines of the Logfile viewer ; messages

 one set when there is good connection 

+ one set when there is a problem 

thanks in advance

---

### Post by cylinderz on 2010-01-24
Thanks for your interest in this. 
I have attached the hsoconnect log below for both an unsuccessful and a successful attempt to browse the web or open my email. Email (thunderbird) reports "failed to connect to [name of account]" of which I have a few. 
my web browser (firefox) reports "server not found" 

Either way hsoconnect reports much the same. There is an additional problem inasmuch as when hsoconnect has been used my pc often refuses to shutdowwn and has to be sitched off. Ozeroffcd is working fine. Problem seems to be hsoconnect related.  Or I guess it couldbe some kind of driver problem. 30% of time I can connect  70% of time I can't and I have to reboot because once hsoconnect hits a problem if I close it it will not restart. 
log attached

Any ideas? 

Successful attempt
******************

<<_OWANCALL: 1,2>>
<<_OWANCALL: 1,2>>
<<_OWANCALL: 1,1>>
<<_OWANCALL: 1,1>>
Sending ->AT_OWANDATA=1<<AT_OWANDATA=1>>
<<_OWANDATA: 1, 89.195.30.152, 0.0.0.0, 193.36.79.100, 193.36.79.101, 0.0.0.0, 0.0.0.0, 72000>>

======connected======
<<OK>>
Sending ->AT_OWANDATA=1<<AT_OWANDATA=1>>
<<_OWANDATA: 1, 89.195.30.152, 0.0.0.0, 193.36.79.100, 193.36.79.101, 0.0.0.0, 0.0.0.0, 72000>>
<<OK>>
Sending ->AT_OHCIP<<AT_OHCIP>>
<<_OHCIP: 0>>
<<OK>><<_OSIGQ: 4,0>>


Unsuccessful attempt
********************

<<_OWANCALL: 1,2>>
<<_OWANCALL: 1,2>>
<<_OSIGQ: 4,0>>
<<_OWANCALL: 1,1>>
<<_OWANCALL: 1,1>>
Sending ->AT_OWANDATA=1<<AT_OWANDATA=1>>
<<_OWANDATA: 1, 89.195.73.251, 0.0.0.0, 193.36.79.100, 193.36.79.101, 0.0.0.0, 0.0.0.0, 72000>>

======connected======
<<OK>>
Sending ->AT_OWANDATA=1<<AT_OWANDATA=1>>
<<_OWANDATA: 1, 89.195.73.251, 0.0.0.0, 193.36.79.100, 193.36.79.101, 0.0.0.0, 0.0.0.0, 72000>>
<<OK>>
Sending ->AT_OHCIP<<AT_OHCIP>>
<<_OHCIP: 0>>
<<OK>>

---

### Post by alexfish on 2010-01-24
hi

from the terminal can you post the output of this code : after you have made the connection

Code:

 egrep -v '#|^ *$' /etc/ppp/options

thanks in advance

---

### Post by cylinderz on 2010-01-25
The mystery deepens. 

egrep -v '#|^ *$' /etc/ppp/options unfortunately doesn't highlight any kind of difference. 
For the sake of completeness here they are:

dongle connection that works

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

dongle connection which doesn't work

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

what I have also noticed is that clicking "disconnect" button often doesn't write anything at all to the diagnostic log on hsoconnect. I guess this means that it's not actually disconnecting. 
I have come up with a sort of a "work around" for this which allows me to disconnect and try reconnecting. I have set up two identical profiles so that rather than try to disconnect I can switch between them. This does cause it to disconnect and reconnect on the other profile. If I get very lucky I get connection which actually works but how much of my dongle usage is being wasted and not clocked I have no idea

---

### Post by cylinderz on 2010-01-25
Some progress has been made! At least I believe so. 

It's too early for me say for definite that all is well but it seems to be behaving very nicely on two machines. 

With a bit of further research I found this page regarding problems on a quicksilver dongle.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/91686](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/91686)

Although this relates to a different dongle and a different problem there did seem to be some similarities and there was mention of something called resolveconf. 
Consequently I tried this 
sudo apt-get install resolvconf

The result was an immediate improvement. The HSOConnect program will shutdown and start up again and when I click disconnect it reports a disconnect in its log. 
So far (fingers crossed) Everytime that I have tried to connect using the icon 515m it has been successful. 

Laptop is now shutting down successfully after use too. 

I'll update this in a couple of days when I'm absolutely sure that the problem is resolved. Many thanks for the assistance so far and also thanks everyone who takes the time and trouble to write these utilities.

---

### Post by cylinderz on 2010-01-26
Dongle is now connecting every time. No more unpredictability. 

sudo apt-get install resolvconf   has made a world of difference. 
so I would advise anyone else who tries to get this dongle going to consider installing resolvconf once all the other steps have been worked through.

---

### Post by alexfish on 2010-01-29
> **cylinderz said:**
> Dongle is now connecting every time. No more unpredictability. 

sudo apt-get install resolvconf   has made a world of difference. 
so I would advise anyone else who tries to get this dongle going to consider installing resolvconf once all the other steps have been worked through.


Hi

This program may want to remove the Gnome ppp ; Therefore reducing options for connections

try editing the [B]/etc/resolv.conf file  first

[/B]   	 	 	 	 	 	  [**How to :Modify new name server address(NS1/NS2)**]("http://ubuntuforums.org/showpost.php?p=8664426&postcount=6")

---

### Post by Pharscape on 2010-03-15
Hi All,

The Icon 5x5 range had some problems with the standard hso driver shipping with current Ubuntu versions. HSO version 1.14 posted on my site is the best way to go.

The official Option 1.14 driver is not compatible with Ubuntu 9.10 yet so I have backported the 2.6.33 hso driver to 2.6.31 (used in 9.10). This works fine for me and is temporary as I expect Option to release an official driver for 9.10 soon.

FYI - if you are using HSOconnect or NetworkManager to connect to the Internet then PPP is not used so PPPD options dont apply. The Icon range of devices provide an Ethernet like interface. You can use PPP if you prefer (on some devices at least), just have a look at the README shipping with the HSO driver for details.


Cheers,
Paul

---

### Post by ugm6hr on 2010-05-30
Any experience with 10.04 with this modem yet?

I use an O2 dongle, that works flawlessly, but like the £5 / month offer Orange have for mobile phone customers.

But I need to ensure the modem will work before investing.

---

### Post by pdc on 2010-05-30
can you not negotiate a "try before you buy" deal with them: valuable for others to learn; I see pharscape from ozerocdoff is now registered as forum member; valuable backup there ..

as you are ubuntu forum staff?

---

### Post by alexfish on 2010-05-31
> **ugm6hr said:**
> Any experience with 10.04 with this modem yet?

I use an O2 dongle, that works flawlessly, but like the £5 / month offer Orange have for mobile phone customers.

But I need to ensure the modem will work before investing.

Hi

the only comment I could make is that to follow advice given by PDC,

 The Main difference of the OPTION device, is the " AT_OWANCALL" , use with reference to post #11

**Command**: AT_OWANDATA=<pdp context>
**Response**:  _OWANDATA: <pdp context>, <ip address>, <route?>,  <nameserver 1>, <nameserver 2>, <unknown>,  <unknown>, <speed>
**Description**: Retrieve  IP configuration from an established connection previously created with  AT_OWANCALL
**Example**:[INDENT]>AT_OWANDATA=1
_OWANDATA:  1, 79.138.181.171, 0.0.0.0, 80.251.192.244, 80.251.192.245, 0.0.0.0,  0.0.0.0, 72000
[/INDENT]so if the device is recocognised as HSO then your best option {not a pun} is to use the hso drivers from Pharescape , this will will save you from having to make your own script.

The only area of which I don't agree on with the present HSO connect is the necessity to install third party software IE: the RESOLVECONF .If you have to rely on gnomepp or wvdial then the Resolvconf will want to remove these,so this is an area of conflict ,see below

As you are using o2 for your connection there could be an area of conflict not only associated with 10.04 but may also apply  other versions of Ubuntu ,

In some instances Depending on the make or version of the device, there maybe more than one control line , if for any reason the Modem-Manager is returning the wrong enumeration for the device, then as a workaround users have to resort to other means of dial up.IE gnomeppp 

From the above you may be faced with having to make a choice.

One possible workaround would be to install Sakis3g , but as yet untested
details can be found here ; post #10

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

regards

alexfish

---

### Post by ugm6hr on 2010-05-31
> **pdc said:**
> as you are ubuntu forum staff?

I am fairly confident that Orange's response will be unhelpful - they state their "compatibility" (i.e. MS / Apple) on their site.

Might give it a try if I can find someone sufficiently senior to email.

Was just curious if someone who already has the device has tried with 10.04...

---

### Post by jarviser on 2010-06-01
Orange UK would not recognize the words "try before you buy" (or "Linux" for that matter.) They will only offer a 1 month contract which can be upgraded but will cost GBP49.99 + 10 a month. If you don't renew, that's a ver expensive locked dongle to put on ebay.
When I wanted to try out mobile BB at my home that was the only option available. They said that with any contract if any data had been downloaded (even at dial-up speed) then the service and the contract would be deemed to have been accepted and irrevocable. Even UK distance selling regulations does not cover contracted services, but it might cover the dongle if it went to court.
The only provider offering me a 14 day trial was "3" when ordered online.

Orange Huawei E160E works.

---

### Post by Joshimitsu on 2010-06-19
Hey everyone, noob here.

I installed ozerocdoff utility successfully (I think) but nothing seems to happen when I try to install hsoconnect.  After the install is it not supposed to show up under Applications/Internet menu?  It's not there.

I'm trying to use the Icon 515 from Orange on my Samsung NC10 Netbook with Ubuntu 10.04.  Any advice would be appreciated.

Thanks!
Josh

---

### Post by alexfish on 2010-06-19
> **Joshimitsu said:**
> Hey everyone, noob here.

I installed ozerocdoff utility successfully (I think) but nothing seems to happen when I try to install hsoconnect.  After the install is it not supposed to show up under Applications/Internet menu?  It's not there.

I'm trying to use the Icon 515 from Orange on my Samsung NC10 Netbook with Ubuntu 10.04.  Any advice would be appreciated.

Thanks!
Josh


Hi 
there is a Pharscape forum here

[http://www.pharscape.org/forum/index.php](http://www.pharscape.org/forum/index.php)

regards

alexfish

---

### Post by Forrest1988 on 2011-03-20
Hi

I've got problem with my Option 515m. I changed configuration file for usb_modeswitch (in /etc/usb-modeswitch.conf) and added:

> 
#######################################################
# Option HSO device

DefaultVendor   =0x0af0
DefaultProduct  =0xd001

TargetVendor    =0x0af0
TargetProduct   =0xd157

TargetClass =0xff

Interface   =0x01

MessageEndpoint =0x02

ResponseEndpoint =0x89

MessageContent  =55534243785634120100000080000601000000000000000000000000000000

CheckSuccess    =4


I didn't help.
I installed udev and HSOconnect (it works but doesn't see my modem). 
Than I edited /etc/udev/rules.d/51-hso-udev.rules file and added (in the right place):

> 
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d055", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}"


I saved, rebooted and ... still doesn't work.

In syslog file after pluging in my modem I can see something like that:

> 
Mar 20 19:21:26 PC-Luk kernel: [ 1264.500016] usb 1-5: new high speed USB device using ehci_hcd and address 78
Mar 20 19:21:27 PC-Luk kernel: [ 1265.024033] usb 1-5: device not accepting address 78, error -71
Mar 20 19:21:27 PC-Luk kernel: [ 1265.136026] usb 1-5: new high speed USB device using ehci_hcd and address 79
Mar 20 19:21:27 PC-Luk kernel: [ 1265.279554] generic-usb 0003:0AF0:D001.01C4: hiddev96,hidraw0: USB HID v1.10 Device [Option Wireless Technology GlobeTrotter GI1515] on usb-0000:00:10.3-5/input0
Mar 20 19:21:27 PC-Luk kernel: [ 1265.282211] scsi450 : usb-storage 1-5:1.1
Mar 20 19:21:28 PC-Luk kernel: [ 1266.280879] scsi 450:0:0:0: CD-ROM            ZCOption Icon CD          1.00 PQ: 0 ANSI: 4
Mar 20 19:21:28 PC-Luk kernel: [ 1266.282092] scsi 450:0:0:1: Direct-Access     ZCOPTION Icon SD Reader   1.00 PQ: 0 ANSI: 4
Mar 20 19:21:28 PC-Luk kernel: [ 1266.288758] sr1: scsi-1 drive
Mar 20 19:21:28 PC-Luk kernel: [ 1266.289058] sr 450:0:0:0: Attached scsi CD-ROM sr1
Mar 20 19:21:28 PC-Luk kernel: [ 1266.289207] sr 450:0:0:0: Attached scsi generic sg2 type 5
Mar 20 19:21:28 PC-Luk kernel: [ 1266.289458] sd 450:0:0:1: Attached scsi generic sg3 type 0
Mar 20 19:21:28 PC-Luk kernel: [ 1266.300667] usb 1-5: USB disconnect, address 79


Mar 20 19:21:28 PC-Luk kernel: [ 1266.331226] sd 450:0:0:1: [sdb] READ CAPACITY failed
Mar 20 19:21:28 PC-Luk kernel: [ 1266.331237] sd 450:0:0:1: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Mar 20 19:21:28 PC-Luk kernel: [ 1266.331244] sd 450:0:0:1: [sdb] Sense not available.
Mar 20 19:21:28 PC-Luk kernel: [ 1266.331268] sd 450:0:0:1: [sdb] Write Protect is off
Mar 20 19:21:28 PC-Luk kernel: [ 1266.331273] sd 450:0:0:1: [sdb] Mode Sense: 00 00 00 00
Mar 20 19:21:28 PC-Luk kernel: [ 1266.331278] sd 450:0:0:1: [sdb] Assuming drive cache: write through
Mar 20 19:21:28 PC-Luk kernel: [ 1266.335028] sd 450:0:0:1: [sdb] READ CAPACITY failed
Mar 20 19:21:28 PC-Luk kernel: [ 1266.335037] sd 450:0:0:1: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Mar 20 19:21:28 PC-Luk kernel: [ 1266.335043] sd 450:0:0:1: [sdb] Sense not available.
Mar 20 19:21:28 PC-Luk kernel: [ 1266.335068] sd 450:0:0:1: [sdb] Assuming drive cache: write through
Mar 20 19:21:28 PC-Luk kernel: [ 1266.335076] sd 450:0:0:1: [sdb] Attached SCSI removable disk
Mar 20 19:21:28 PC-Luk kernel: [ 1266.576040] usb 1-5: new high speed USB device using ehci_hcd and address 80
Mar 20 19:21:28 PC-Luk kernel: [ 1266.719610] generic-usb 0003:0AF0:D001.01C5: hiddev96,hidraw0: USB HID v1.10 Device [Option Wireless Technology GlobeTrotter GI1515] on usb-0000:00:10.3-5/input0
Mar 20 19:21:28 PC-Luk kernel: [ 1266.722256] scsi451 : usb-storage 1-5:1.1
Mar 20 19:21:29 PC-Luk kernel: [ 1267.720961] scsi 451:0:0:0: CD-ROM            ZCOption Icon CD          1.00 PQ: 0 ANSI: 4
Mar 20 19:21:29 PC-Luk kernel: [ 1267.722171] scsi 451:0:0:1: Direct-Access     ZCOPTION Icon SD Reader   1.00 PQ: 0 ANSI: 4
Mar 20 19:21:29 PC-Luk kernel: [ 1267.729834] sr1: scsi-1 drive
Mar 20 19:21:29 PC-Luk kernel: [ 1267.730121] sr 451:0:0:0: Attached scsi CD-ROM sr1
Mar 20 19:21:29 PC-Luk kernel: [ 1267.730269] sr 451:0:0:0: Attached scsi generic sg2 type 5
Mar 20 19:21:29 PC-Luk kernel: [ 1267.730515] sd 451:0:0:1: Attached scsi generic sg3 type 0
Mar 20 19:21:29 PC-Luk kernel: [ 1267.765529] sd 451:0:0:1: [sdb] Attached SCSI removable disk
Mar 20 19:21:30 PC-Luk kernel: [ 1268.344758] usb 1-5: USB disconnect, address 80


It shows continuously until I unplug it. 

What's I've done wrong? Can anyone help me?

Thanks in advance

---

### Post by alexfish on 2011-03-20
Hi

if using usb_modeswitch the have to edit the usb_modeswitch data and the usb_modeswitch rules

can try disable the ozercdoff rules then make the following
```
sudo gedit /etc/usb_modeswitch.d/0af0:d001
``` copy and paste your info

```
################################################## #####
# Option HSO device

DefaultVendor =0x0af0
DefaultProduct =0xd001

TargetVendor =0x0af0
TargetProduct =0xd157

TargetClass =0xff

Interface =0x01

MessageEndpoint =0x02

ResponseEndpoint =0x89

MessageContent ="55534243785634120100000080000601000000000000000000000000000000"

CheckSuccess =4
``` save and exit

then edit the modeswitch rules
```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
``` add these lines
```
# option device 0af0:d001
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d001", RUN+="usb_modeswitch '%b/%k'"
```see what happens

---

### Post by Forrest1988 on 2011-03-21
I did this but I still see something like that:

> 
**lukas@PC-Luk:~$ lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 075: ID 0af0:d001 Option **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**lukas@PC-Luk:~$ tail -f /var/log/syslog**

Mar 21 08:20:03 PC-Luk kernel: [  151.760018] usb 1-5: new high speed USB device using ehci_hcd and address 101
Mar 21 08:20:04 PC-Luk kernel: [  152.288023] usb 1-5: device not accepting address 101, error -71

Mar 21 08:20:04 PC-Luk kernel: [  152.400041] usb 1-5: new high speed USB device using ehci_hcd and address 102
Mar 21 08:20:04 PC-Luk kernel: [  152.543488] generic-usb 0003:0AF0:D001.003C: hiddev96,hidraw0: USB HID v1.10 Device [Option Wireless Technology GlobeTrotter GI1515] on usb-0000:00:10.3-5/input0
Mar 21 08:20:04 PC-Luk kernel: [  152.545814] scsi58 : usb-storage 1-5:1.1
Mar 21 08:20:05 PC-Luk kernel: [  153.660020] usb 1-5: reset high speed USB device using ehci_hcd and address 102
Mar 21 08:20:06 PC-Luk kernel: [  153.908027] usb 1-5: reset high speed USB device using ehci_hcd and address 102
Mar 21 08:20:06 PC-Luk kernel: [  153.976354] usb 1-5: USB disconnect, address 102

Mar 21 08:20:06 PC-Luk kernel: [  154.220067] usb 1-5: new high speed USB device using ehci_hcd and address 103
Mar 21 08:20:06 PC-Luk kernel: [  154.363622] generic-usb 0003:0AF0:D001.003D: hiddev96,hidraw0: USB HID v1.10 Device [Option Wireless Technology GlobeTrotter GI1515] on usb-0000:00:10.3-5/input0
Mar 21 08:20:06 PC-Luk kernel: [  154.366230] scsi59 : usb-storage 1-5:1.1
Mar 21 08:20:07 PC-Luk kernel: [  155.480019] usb 1-5: reset high speed USB device using ehci_hcd and address 103
Mar 21 08:20:07 PC-Luk kernel: [  155.624225] usb 1-5: device descriptor read/all, error -71
Mar 21 08:20:07 PC-Luk kernel: [  155.740027] usb 1-5: reset high speed USB device using ehci_hcd and address 103
Mar 21 08:20:08 PC-Luk kernel: [  155.808403] usb 1-5: USB disconnect, address 103

Mar 21 08:20:08 PC-Luk kernel: [  156.052018] usb 1-5: new high speed USB device using ehci_hcd and address 104
Mar 21 08:20:08 PC-Luk kernel: [  156.195591] generic-usb 0003:0AF0:D001.003E: hiddev96,hidraw0: USB HID v1.10 Device [Option Wireless Technology GlobeTrotter GI1515] on usb-0000:00:10.3-5/input0
Mar 21 08:20:08 PC-Luk kernel: [  156.198279] scsi60 : usb-storage 1-5:1.1
Mar 21 08:20:09 PC-Luk kernel: [  157.312038] usb 1-5: reset high speed USB device using ehci_hcd and address 104
Mar 21 08:20:09 PC-Luk kernel: [  157.560023] usb 1-5: reset high speed USB device using ehci_hcd and address 104
Mar 21 08:20:10 PC-Luk kernel: [  158.080022] usb 1-5: device not accepting address 104, error -71
Mar 21 08:20:10 PC-Luk kernel: [  158.192028] usb 1-5: reset high speed USB device using ehci_hcd and address 104
Mar 21 08:20:10 PC-Luk kernel: [  158.440023] usb 1-5: reset high speed USB device using ehci_hcd and address 104
Mar 21 08:20:10 PC-Luk kernel: [  158.688040] usb 1-5: reset high speed USB device using ehci_hcd and address 104
Mar 21 08:20:11 PC-Luk kernel: [  159.706907] usb 1-5: USB disconnect, address 104
What can be wrong?

---

### Post by alexfish on 2011-03-21
hi

will need to take a fresh look at this , there have been several changes at kernel level upto Ubuntu Meerkat (original thread started as regards Ubuntu 9.10)

so need version of Ubuntu been used ,

and results of

```
uname -a
```can also give the source of info posted as regards the usb_modeswitch 
are you booting from internal harddrive / ext usb harddrive / usbstick ?
alexfish

---

### Post by Forrest1988 on 2011-03-22
I use Ubuntu 10.10 - the Maverick Meerkat (Oct 2010) installed on my hd.

uname -a gave me:

> 
Linux PC-luk 2.6.35-23-generic #41-Ubuntu SMP Web Nov 24 10:18:49 UTC 2010 i686 GNU/Linux


Source of my usb_modeswitch config is:

> 
[http://skynet.elektroda.eu/index.php/2010/08/10/orange-option-icon-515m/](http://skynet.elektroda.eu/index.php/2010/08/10/orange-option-icon-515m/)


Thanks for helping me ;)

---

### Post by alexfish on 2011-03-26
> **Forrest1988 said:**
> I use Ubuntu 10.10 - the Maverick Meerkat (Oct 2010) installed on my hd.

uname -a gave me:



Source of my usb_modeswitch config is:



Thanks for helping me ;)
Hi

only thing can suggest is to date the system to latest kernels, see what happens

kernel now at (2.6.35-28.)

from the info posted , looks as if the device is continually connecting and disconnecting
and the system is not settling , possible this could lead to a system crash,

also not sure if this device may switch by issuing an eject command ,

but first need to see if the device will remain stable,
has the device been configured in windows (and stable) , if not suggest to do so

if after updates and if the device has been configured in windows will look further

if the device is still looping , will have to look at dissabling the usb_modeswitch 

did you also install ozercdoff (yes or no) , or any other rules

also need to know if any other software been installed as regard connection managers

Added : can also monitor udisks events 
```
udisks --monitor
```then connect the device
and post the results


alexfish

---

### Post by Forrest1988 on 2011-03-27
I started with the instruction from **[http://www.pharscape.org/forum/index.php/topic,809.0.html](http://www.pharscape.org/forum/index.php/topic,809.0.html)**

> 
Install the ozerocdoff utility:
1. Download the udev-icon5x5-pharscape-091208.tar.gz
2. Untar the file:  tar zxf udev-icon5x5*
3. Change to the udev directory: cd udev*
4. Install the udev rules: sudo make install
5. Reboot (to reload the rules!)

Install hsolinkcontrol: [http://www.pharscape.org/hsolinkcontrol.html](http://www.pharscape.org/hsolinkcontrol.html)

Install hsoconnect:
1. Download the hsoconnect-1.2.19.tar.gz file
2. Untar the file : tar zxf hsoconnect*
3. Change to the hsoconnect directory : cd hsoconnect*
3.1. Patching: patch Makefile < SiB.txt
4. Install hsoconnect : sudo make install

To use it:

1. Disable NetworkManager Wireless (right mouse button menu).
2. Run HSOconnect from the Applications/Internet menu.


It was a problem with config so I installed hsolink from **[http://www.pharscape.org/hsolinkcontrol.html](http://www.pharscape.org/hsolinkcontrol.html)**
HSOconnect turned on and worked but it didn't detect any device like modem.

In console I saw this:

> 
**root@pc:/home/lukas/Solution/hsolink-1.0.118# udisks --monitor**
added:     /org/freedesktop/UDisks/devices/sdb
added:     /org/freedesktop/UDisks/devices/sr1
removed:   /org/freedesktop/UDisks/devices/sdb
removed:   /org/freedesktop/UDisks/devices/sr1
added:     /org/freedesktop/UDisks/devices/sr1
added:     /org/freedesktop/UDisks/devices/sdb
removed:   /org/freedesktop/UDisks/devices/sdb
removed:   /org/freedesktop/UDisks/devices/sr1

**root@pc:~# lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 116: ID 0af0:d001 Option 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I changed **/etc/usb_modeswitch.conf** as I wrote before.
Edited file **/etc/usb_modeswitch.d/0af0:d001** and **/lib/udev/rules.d/40-usb_modeswitch.rules**
From syslog I could see:

> 
Mar 27 15:04:26 pc kernel: [ 1386.724019] usb 1-6: new high speed USB device using ehci_hcd and address 125
Mar 27 15:04:27 pc kernel: [ 1386.792358] hub 1-0:1.0: unable to enumerate USB device on port 6
Mar 27 15:04:27 pc kernel: [ 1386.976340] hub 1-0:1.0: unable to enumerate USB device on port 6
Mar 27 15:04:27 pc kernel: [ 1387.216019] usb 1-6: new high speed USB device using ehci_hcd and address 127
Mar 27 15:04:27 pc kernel: [ 1387.284299] hub 1-0:1.0: unable to enumerate USB device on port 6
Mar 27 15:04:27 pc kernel: [ 1387.524019] usb 1-6: new high speed USB device using ehci_hcd and address 2
Mar 27 15:04:27 pc kernel: [ 1387.592389] hub 1-0:1.0: unable to enumerate USB device on port 6
Mar 27 15:04:28 pc kernel: [ 1387.832019] usb 1-6: new high speed USB device using ehci_hcd and address 3
Mar 27 15:04:28 pc kernel: [ 1387.900353] hub 1-0:1.0: unable to enumerate USB device on port 6
Mar 27 15:04:28 pc kernel: [ 1388.140019] usb 1-6: new high speed USB device using ehci_hcd and address 5
Mar 27 15:04:28 pc kernel: [ 1388.208316] hub 1-0:1.0: unable to enumerate USB device on port 6
Mar 27 15:04:28 pc kernel: [ 1388.392299] hub 1-0:1.0: unable to enumerate USB device on port 6


**udisks --monitor** gave nothing so I changed **/etc/udev/rules.d/51-hso-udev.rules** as I wrote before for ozerocdoff but it didn't changed anything. Now I can't see Option using **lsusb** because it is still connecting and disconnecting all the time.

I use it with Windows XP and Windows 7 and it works very good so I am sure that modem is OK.

---

### Post by alexfish on 2011-03-28
hi Forest1988

bit late in posting , done a lot of reading
at pharscape site there are several softwares and versions of different make ups, in main only go to kernel level 2.6.34 (this
includes kernel patches ) not required in kernels above (including Ubuntu 10.10) as your device ID is included in the kernel module

to cut short , need further info

did the device behave the same as regards the continual looping of connecting and disconnecting

can post full list and versions of the sofware (Not the links) installed from the pharescape site , + if any other software you have tried to install

the version of usb_modeswitch and the source (ubuntu repos , debian , tar file source code)
version of modeswitch can be obtained with this command
usb_modeswitch -e

from the inf will look at the options to try and rectify (mainly will look at the udev rules or kernel patchs if any + removal of ozerocdoff),
but do not remove anything at present), reason for removal of ozerocdoff , site seams to indicate use usb_modeswitch for newer devices ,

this will also have to be looked at if the device continues to be a problem ( if sd card inserted try removing before use)

Added :
ADDED : the hsolink control for Ubuntu (version ) only available upto  Ubuntu 10.04 , so not sure where heading in Ubuntu 10.10 ( it may or may  not work ? )
........... or possible the network manager will pick up the device ?

alexfish

---

### Post by azurite320 on 2011-05-24
Getting this dongle to work was difficult. 
 
I managed it once for a short period. It would then not connect. 
 
I have now upgraded to 11.04 and it works instantly ..... just plug it in. Great!

---

