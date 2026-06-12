---
title: "How to set up wireless internet in Ubuntu"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by Slavek_D on 2010-08-01
Hi,
I am not sure if this subject was already discussed (I couldn't find it) but can you please provide me step by step guideline how to set up wireless connection in Ubuntu? Wireless router is already set up because wireless internet was working fine on my laptop befoe I installed Ubuntu and it works on my second laptop.

---

### Post by dv3500ea on 2010-08-01
Click on the wireless connections icon in the top right hand corner, select your wireless connection and enter the password if you need one.

---

### Post by Slavek_D on 2010-08-01
But I don't have wireless connections there. I think I have to set up one first...

---

### Post by Slavek_D on 2010-08-01
There are 4 tabs:
Wireless
Wireless Security
IPv4 Settings
and IPv6 Settings

I have no clue what I should change. Setting the same in Windows was extremely easy. System was able to find connections itself. I only had to enter the password...

---

### Post by cavalier911 on 2010-08-01
Before you can setup the connection  you have to determine the identity of the wireless adapter,find the correct linux driver module and load it. 
On the slim chance this was done automagically open terminal and type ifconfig followed by enter,post the output.

---

### Post by gordintoronto on 2010-08-01
What wireless adapter (brand and model) do you have? It should show up in the output from lspci or lsusb

---

### Post by Slavek_D on 2010-08-02
I use EchoLife HG520s and it perfectly works with other devices

---

### Post by gordintoronto on 2010-08-02
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

---

### Post by Slavek_D on 2010-08-03
Well, if I had this menu everything would be very simple.
All I have in System->Administrator->Network is a 'Network Settings' window with 3 tabs (General, DNS, Hosts) and a padlock with 'Click to make changes'. When you click you can edit the text boxes. Unfortunately I cannot see any icons or simple settings as they are described in the link you gave me.

---

### Post by gordintoronto on 2010-08-04
Do you have a Preferences/Network Connections?

---

### Post by gordintoronto on 2010-08-04
Sorry, I looked at the Community Docs again, and they are all completely out of date.  On my system, I can select Preferences/Network Connections, click the Wireless tab, then click "add," enter my router's SSID, then select "wireless security," where I select the encryption type and enter the password. Click the "all users" box, then OK. All done.

---

### Post by Slavek_D on 2010-08-04
> **gordintoronto said:**
> Sorry, I looked at the Community Docs again, and they are all completely out of date.  On my system, I can select Preferences/Network Connections, click the Wireless tab, then click "add," enter my router's SSID, then select "wireless security," where I select the encryption type and enter the password. Click the "all users" box, then OK. All done.

Thank you but when I click on Wireless I must type the following:

[LIST]
[*]SSID - OK
[*]BSSID - ??? (is it the same as Broadcast SSID? If yes I have only Yes/No options on my router's settings whereas I think something else is required :(
[*]MAC address - ??? (again in my router settings I can see only Active Enable or Disable
[*]MTU (automatic?)
[/LIST]
 
When I click on 'Wireless Security' I have 6 options and I don't really know which one I should choose :(

Can you help?

---

### Post by Slavek_D on 2010-08-04
Ok I found MAC address but I still don't know how to find all the rest...

---

### Post by gordintoronto on 2010-08-04
The wireless security is set up on the router. It should be WPA with a reasonably good password. A router which is at "factory settings" will have no security, which invites all your neighbours to download on your dime.

---

### Post by jcolyn on 2010-08-04
First you have to setup the router by giving it a name such as Ubuntu then setup wireless security. I use WPA & WPA Personal by entering a long password. Restart the router.

Next from your desktop go to system-preferences-network connections. Click on the wireless tab and click the add button. SSID should be named the same name you entered in the router. Mode will probably be Infrastructure since most routers are. MTU will be automatic. Next click the wireless security tab. Under security set it as WPA & WPA Personal if that is the security you set in the router then enter the same password you set in the router and click apply.

You should then have wireless working..

---

### Post by Slavek_D on 2010-08-05
Thank you. I think I am nearly there because I found the following settings:
SSID - fine
MTU - fine
MAC address - fine

Unfortunately I still cannot find any information about my BSSID on my router's settings :(

Can you help?

---

### Post by jcolyn on 2010-08-05
> **Slavek_D said:**
> 
Unfortunately I still cannot find any information about my BSSID on my router's settings :(

Can you help?

If I'm not mistaken this is an optional setting in most routers. It's purpose if used is to hide your router from others. I leave mine blank..

---

### Post by Slavek_D on 2010-08-05
I am still struggled. I have following settings (data taken from my router):

**Wireless:**
SSID - 00:16:E3........
MTU - automatic
MAC address - name_of_my_network
BSSID - blank

**IPv4 Settings** - Automatic (DHCP)

**IPv6 Settings** - Ignore

**Wireless Security** - the same as I found on my router (WEP 40/128-bit Key

And wireless network does not work. Help please!

---

### Post by gordintoronto on 2010-08-05
Did you enter the WEP key which is set up on the router? On the screen where you enter it, there is a check-box to display the key as you type it. I always turn that on, because my typing is not perfect.

Oops, your SSID is wrong. It should be the Router's name. Leave the Mac address blank.

---

### Post by jcolyn on 2010-08-05
> **Slavek_D said:**
> I am still struggled. I have following settings (data taken from my router):

**Wireless:**
SSID - 00:16:E3........
MTU - automatic
MAC address - name_of_my_network
BSSID - blank

**IPv4 Settings** - Automatic (DHCP)

**IPv6 Settings** - Ignore

**Wireless Security** - the same as I found on my router (WEP 40/128-bit Key

And wireless network does not work. Help please!

SSID should be the name you entered in the SSID box in the router. Any name will do such as Ubuntu. MAC leave it blank. 

Wireless security: I'd change that in the router to WPA WPA2 and choose Personal then enter a password and confirm it

Also in the Wireless setting settings if you have a box enable wireless: it needs to be checked.

---

### Post by Slavek_D on 2010-08-06
I followed your advices but I am still struggled. I have following settings now:

**Wireless:**
SSID - name_of_my_network
Mode - Infrastructure
BSSID - blank
MAC address - blank
MTU - automatic


**IPv4 Settings** - Automatic (DHCP)

**IPv6 Settings** - Ignore

**Wireless Security** - WPA & WPA2 Personal

And wireless network still does not work. 

Help please!

---

### Post by gordintoronto on 2010-08-06
> **Slavek_D said:**
> I followed your advices but I am still struggled. I have following settings now:

**Wireless:**
SSID - name_of_my_network
Mode - Infrastructure
BSSID - blank
MAC address - blank
MTU - automatic


**IPv4 Settings** - Automatic (DHCP)

**IPv6 Settings** - Ignore

**Wireless Security** - WPA & WPA2 Personal

And wireless network still does not work. 

Help please!

The SSID is the name of the router! When the router was set up, it was filled in. Do you have control of the router?

You also need to specify security settings.

---

### Post by Slavek_D on 2010-08-07
I know SSID is the same as name of my router (MyTalkTalk). I found it in my router settings:
Basis->Wireless Lan: SSID: MyTalkTalk but it is still not working.

Security settings were also specified because wireless works fine on other machines with Windows when I use my password...

I don't want to give up at this stage :)

---

### Post by gordintoronto on 2010-08-07
> **Slavek_D said:**
> Security settings were also specified because wireless works fine on other machines with Windows when I use my password...



I can't figure out what you're trying to say. Did you put the router password into Network Manager?

---

### Post by Slavek_D on 2010-08-08
When I go to my router options (Basic->Wireless Lan) I can see Authentication type: WEP-128 Bits so I am assuming I should set up the same in my Ubuntu Wireless settings. Therefore I have following settings now:

**Wireless:**
SSID - MyTalkTalk
Mode - Infrastructure
BSSID - blank
MAC address - blank
MTU - automatic


**IPv4 Settings** - Automatic (DHCP)

**IPv6 Settings** - Ignore

**Wireless Security** - WEP-128-bit Passphrase


What is wrong? I still cannot use my wireless connection :(

---

### Post by gordintoronto on 2010-08-09
Do you have control over the router? What WEP password did you tell the router to use? You must specify the same password in Network Manager.

---

### Post by Slavek_D on 2010-08-09
There is only one password I use for all my wi-fi devices and they all work apart from my laptop with Ubuntu...

---

### Post by Slavek_D on 2010-08-15
So can anyone help me? Is this issue really hopeless? It looked like something easy to do...

---

### Post by Slavek_D on 2011-01-16
> **Slavek_D said:**
> So can anyone help me? Is this issue really hopeless? It looked like something easy to do... Maybe we could start from scratch? I have a fresh Ubuntu installation and I have recently found [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) but it does not work. It is so simple in Windows...It must be an easy step by step guide...

---

### Post by m0nty75 on 2011-06-07
i had trouble with ubuntu on my friends network, he used WEP or WPA

the solution in my case was to get him to reconfigure his router to use  WP2  and AES encryption (not tkip) & not wep or wpa. it then connected 1st time after the password prompt popped up.

wpa2 is far more secure anyway so you'll benefit from using that anyway. wep & wpa are about as secure as a paper window.

i also use hg520s router at home with the same settings above.

---

