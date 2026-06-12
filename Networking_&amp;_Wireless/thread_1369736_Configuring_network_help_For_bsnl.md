---
title: "Configuring network help For bsnl"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by joy23 on 2010-01-01
I live in india.
I am using Karmic.
gfx -- Nvidia 9500.
i have a BSNL(Dataone) broadband connection(i use on windows)
how can i access internet through linux
Modem --  DNA-A211-1   given to me from BSNL.

Now the problem is i am a Newbie and am not able to configure it properly using tools.

Can anyone help and provide me with step by step instructions to access my modem/router  also the internet on Karmic. :confused::confused:

also facing trouble in installing drivers ask for it each and everytime i access almost all programs(Except inbuilt main prgs)

---

### Post by dineshs on 2010-01-04
try this
open firefox
1.Type 192.168.1.1 in Address bar. Click GO
2.Enter both Username and Password as *admin*
3.Click OK
4.Click wireless on left
5.Click security
6.select WPA_PSK as authentication type
7.give WPA-PSK Key (secret wi-fi key 8 alphanumeric password)
8.Click apply
9.Click advanced setup on the left
10.Click *edit* at the right end of the line having 0/35 as VPI/VCI value
11.Click Next
12.select PPP over Ethernet and click next
13.Enter  PPP Username and PPP Password as allotted by BSNL in the respective fields 
14.Click Next
15.Click Next again
16.Click save
17.Click save/reboot
18.wait till reboot complete (3 minutes)
step 4-8 is required only if you are using wifi

---

### Post by joy23 on 2010-01-11
Thanks da for your help
but there's is a problem i can't even access the router
can u just help me in configuring the connection using network management tools available in linux karmic
Also the network settings are bit different on karmic.

---

### Post by dineshs on 2010-01-11
I use 9.04 Anyway try this.
```
sudo gedit /etc/network/interfaces

```
copy and paste this

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Save the file and run this
```
sudo /etc/init.d/networking restart

```
Now try  192.168.1.1 via firefox

---

### Post by dineshs on 2010-01-12
hope these links would be helpful for you.The first one Karmic and second BSNL broadband
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

---

### Post by joy23 on 2010-01-12
> **dineshs said:**
> I use 9.04 Anyway try this.
```
sudo gedit /etc/network/interfaces

```
copy and paste this

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Save the file and run this
```
sudo /etc/init.d/networking restart

```
Now try  192.168.1.1 via firefox


really in neck deep trouble i had recently changed the passwords in XP  (admin/admin) to something else to increase security but it backfired when i forgot them

is there any way to recover lost passwords or reset only the passwords.

i can access internet but can't access the router in XP

in linux can't access both.

can anyone help me in this matter -- ny softwares available in linux or xp.
or by ny method i mean by hook or crook.

---

### Post by dineshs on 2010-01-13
> **joy23 said:**
> changed the passwords in XP  (admin/admin) to something else to increase security but it backfired when i forgot them

You mean the password to access modem? Then the only way out is to reset the modem(Switch on the modem,wait for 2 minutes,Find out the reset button -a hole marked `reset'-in the modem , depress it for 3 seconds ,wait for 3 minutes and reprogram the modem using username admin and password  admin.)
DO THIS ONLY IF YOU KNOW THE USERNAME AND PASSWORD GIVEN BY BSNL because you will need it  in step 13
If you do not know the username and password given by BSNL contact BSNL to get it reset
Anyway you should get 192.168.1.1 once you edit and save /etc/network/interfaces
How do you connect Broadband in XP.With a dialler or directly via IE?

---

### Post by joy23 on 2010-01-14
As of  
> really in neck deep trouble i had recently changed the passwords in XP (admin/admin) to something else to increase security but it backfired when i forgot them

is there any way to recover lost passwords or reset only the passwords.

i really freaked out since i didn't want to reset the modem and also as i could not access it.
on the current thread/topic not much of data is given anywhere and after 5-6hrs of through searching i found that there is no other way than to reset it then in a flash i remembered that i had backed up the config the day it was installed

and 

> You mean the password to access modem? Then the only way out is to reset the modem(Switch on the modem,wait for 2 minutes,Find out the reset button -a hole marked `reset'-in the modem , depress it for 3 seconds ,wait for 3 minutes and reprogram the modem using username admin and password admin.)

i didn't wait for 3 sec though just a press did it
and luckily now i remember that i had backed up the config of router to a file. so settings remain unchanged. effectively changing the password of the router to admin/admin
so what i did was just changed the password and wrote it down somewhere safe.
So moral of the story is [COLOR="Blue"]create a backup of working router configuration with admin/admin as credentials.[/COLOR]
then change the username/password  as required so just incase u forget router password instead of panicking , u can update the router with default config file so infact just same as changing your credentials to default.


Now

> How do you connect Broadband in XP.With a dialler or directly via IE?

the above question is really well answered in many forums regarding XP
also in Microsoft's knowledge base.The bsnl people are real pros regarding this.Just search through google you are sure to get a dependable solution to this.
so just for u in brief  ::: - 

it is not done through ie but mostly using default dialling programs.
right click on My Network places and select properties in that u just have to create a new connection. An interactive GUI will welcome u and then just follow the onscreen instructions and you will be through.
router settings same as that of linux.

Haven't done still with linux ubuntu(karmic)
will get back soon as soon as i access the internet.

---

### Post by joy23 on 2010-01-14
> [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

above links were useful
 nicely maintained

---

### Post by dineshs on 2010-01-15
> **joy23 said:**
> 
it is not done through ie but mostly using default dialling programs.


BSNL Broadband can be connected in 2 ways.(whether it is XP or Linux)
1.ALWAYS ON or PPPoE mode.
In this method you have to configure your modem using the username and password as given by BSNL.This method is easier because you can directly use your web browser 3 minutes after switching on the modem.You dont need a dialler.This was what I explained earlier in 18 steps
2.Bridge mode or using a dialler
This method uses a dialler with which you can connect/disconnect broadband when required(As you said via network places....)But when you configure modem you should select BRIDGE mode in step 12 and step 13 is not required

---

### Post by joy23 on 2010-01-15
i have my modem setup but don't know why it refuses to connect to internet
i can access the modem though linux.
username/password trouble has been sorted out.

i did the below before doing the steps in ur first post.
> I use 9.04 Anyway try this.
Code:
sudo gedit /etc/network/interfaces
copy and paste this

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Save the file and run this
Code:
sudo /etc/init.d/networking restart
Now try 192.168.1.1 via firefox

after this do i need to follow steps given in your first post?
 after doing the above quoted in wired connection it shows "ifupdown"   
and add to it is totally greyed out i.e. we cannot edit it
but after doing that i could access the modem.


 i think i use  
 > 2.Bridge mode or using a dialler
This method uses a dialler with which you can connect/disconnect broadband when required(As you said via network places....)

so is there any similar interface in linux  ? 
after accessing till the modem how do i know the pc connects to the isp in linux? 
in DSL tab i put settings as below

IP             Netmask           Gateway
192.168.1.2   255.255.255.0     "left it blank"

before 
in wired 
192.168.1.1     ""                 ""
but now i can't see this since it is greyed out!
it only shows ifupdown    eth0

now where 2 go from here?

---

### Post by dineshs on 2010-01-16
Since you are using Bridge mode,
In a terminal type
```
sudo pppoeconf
```
and follow instructions (ref [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE))
This will create a file named `dsl-provider' in /etc/ppp/peers
Now to connect broadband use the command 
```
pon dsl-provider
```
And to disconnect use
```
poff dsl-provider
```
If you want to check whether connection is established
```
ifconfig
```
This should show a public  IP address (eg:starting with 117 or 59)as inet address
OR 
```
ping 4.2.2.1
```
should repeat something like this
64 bytes from 4.2.2.1: icmp_seq=1 ttl=47 time=289 ms

Suppose after connecting sites are not loading 
```
sudo gedit /etc/resolv.conf
```
edit and save the file to read this alone
```
nameserver 4.2.2.1
```


I suggest you use PPPoE mode .For this ,since you are getting modem page,follow the 18 steps as explained in first post.If the data/act/internet lamp lights after reboot complete then you can directly browse.(In this mode the device info page in modem will show a public IP as gateway IP when connected)
Suppose after connecting sites are not loading edit /etc/resolv.conf as said above
sudo gedit /etc/resolv.conf

---

### Post by joy23 on 2010-01-20
Thanks a lot
 let me try it out
Will get back to you.

---

### Post by joy23 on 2010-01-22
Still not able to set it up

it says  only dip group users are permitted to do
> Now to connect broadband use the command 
Code:
pon dsl-provider
And to disconnect use
Code:
poff dsl-provider

---

### Post by joy23 on 2010-01-22
also can we download the documentation 
> (ref [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE))

or any such documentation in pdf form?

and is there any difference between pppoe and bridged mode especially in terms of security?

---

### Post by dineshs on 2010-01-22
try this to connect
```
sudo pon dsl-provider
```
you can also add user to dip as this thread says
[https://bugs.launchpad.net/ubuntu/+bug/278828](https://bugs.launchpad.net/ubuntu/+bug/278828)

Regarding the difference between Bridge mode(use dialler to connect) and PPPoE (store username and password in modem) I think PPPoE is more secure
because in Bridge mode,public IP is allotted to PC and hacking becomes easy.

I dont think the document is available in pdf

---

### Post by joy23 on 2010-01-27
i have a laptop running vista
a desktop  dual booting wid   Ubuntu and Xp
i use the above said dailer to connect in Xp
the problem is i donot want to keep my internet connection on always since viruses are always on prowl(my computers are on always about 4-5 hours everyday) so bandwidth is also a problem.
also i need to connect both my laptop and desktop to net .
so pppoe i don't think is a suitable solution for me 
so can u please take me forward in bridging itself.
did whatever u said !
but can connect to router and not internet.
it shows no valid active connections found as of now?
now what to do?

---

### Post by joy23 on 2010-01-27
in Network connections --> wired--->  it has ifupdown(eth0)
which is not editable also
my dsl settings are 

username :  **********
service  :  
password :   **********

_PPP settings_
MPPE unchecked

_Ipv4 settings_
manual

192.168.1.2  255.255.255.0   0.0.0.0

Dns 
search domains     both are blank
DNS

---

### Post by joy23 on 2010-01-27
my laptop's ip is 192.168.1.3

from ubuntu i could connect to vista running lappie

---

### Post by dineshs on 2010-01-27
> **joy23 said:**
> 
also i need to connect both my laptop and desktop to net .


If you want to connect both laptop and Desktop at the same time,Use always on mode.If you use bridge mode you can use only one machine at a time(the machine from which you dialled to connect internet).You can disable ethernet (LAN)when you dont want internet.So what you do is
Connect laptop to one ethernet port of ITI modem and desktop to another.
Configure Ubuntu machine as follows
```
sudo gedit /etc/network/interfaces
```
copy and paste this (The file should contain only this)

```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Save and close the file then run
```
sudo gedit /etc/resolv.conf 
```
copy and paste this (The ip is that of the DSL modem)

```
nameserver 192.168.1.1 
```

Save and close the file
Now open firefox and type 192.168.1.1,follow those 18 steps to configure modem in always on mode as explained earlier.
Now you will be able to access the web
You can disable ethernet by right clicking the network icon on right top corner.

Vista laptop
Do not use dialler,you can directly access the web.Also make a shortcut of local area connection on desktop and disable this when you dont want internet.This will not add usage on your account

Pl post back what happens after following these and whether you are able to get internet on Vista machine.

---

### Post by dineshs on 2010-01-28
pl also let me know whether the `inet' lamp in the modem is glowing after configuring modem in always on mode

---

### Post by joy23 on 2010-01-29
I didn't understand this part
my pc's ip as i said before is 192.168.1.2
> address 192.168.1.100

so do i need to write it as 1.100  or 1.2  in the file?

vista lappie 192.168.1.3  pc 192.168.1.2

will do the rest and get back to you!

---

### Post by dineshs on 2010-01-30
You can assign any IP between 192.168.1.2 to 192.168.1.254 ,only thing donot assign the same IP to 2 machines.

---

### Post by joy23 on 2010-02-05
my vista lappie has crashed don't know why it shows system32/config/software  
blue screen of death
i will be out of action till i get my laptop fixed 
probably 1 or 2 days more
any help here will be appreciated.

---

### Post by joy23 on 2010-02-12
got lappie back on track  so we can continue the discussion

---

### Post by mips on 2010-02-12
joy23,

Just follow this guide: [http://en.kioskea.net/faq/5958-bsnl-wifi-iti-dna-a211-1-setup](http://en.kioskea.net/faq/5958-bsnl-wifi-iti-dna-a211-1-setup)

This way you don't have to worry about setting up PPPoE dialers in windows or linux. You will have a always on connection via your ethernet port.

Tags: BSNL DNA-A211-1 India Internet

---

### Post by joy23 on 2010-02-13
Thanks mips for replying 
The thing you talking about is the same thing that Dinesh was saying 
but i don't want my connection to be always on
also i want to connect my vista lappie(192.168.1.3) and Xp/Linux Desktop(192.168.1.2)
which i am finding it difficult

---

### Post by mips on 2010-02-13
> **joy23 said:**
> 
but i don't want my connection to be always on
also i want to connect my vista lappie(192.168.1.3) and Xp/Linux Desktop(192.168.1.2)
which i am finding it difficult

Why not? If you don't use it no traffic goes through?
With the link I gave you all you would have to do on your Vista/xp/linux pc's is enable dhcp and that's it.

---

### Post by joy23 on 2010-02-14
what about if i want to operate LAN and not the internet what about security issues?

---

### Post by dineshs on 2010-02-15
I believe internet is never 100 percent secure.You can make it secure to some extent using Linux,installing antivirus using firewall etc.If you want LAN but not internet,just unplug the ADSL line from modem.Your LAN will work

---

### Post by mips on 2010-02-15
> **joy23 said:**
> what about if i want to operate LAN and not the internet what about security issues?

I don't follow, what about the LAN? How do things change at all when it's connected to the internet?

So you are happy with the security while you make the connection but not when it's automatic?

Sorry, I cannot help you, maybe someone else will come along with a solution to your problem.

---

### Post by joy23 on 2010-02-15
That seems to be viable .. mm 
Let me go through all of it and i will report back!

---

### Post by joy23 on 2010-02-16
> **mips said:**
> I don't follow, what about the LAN? How do things change at all when it's connected to the internet?

So you are happy with the security while you make the connection but not when it's automatic?

Sorry, I cannot help you, maybe someone else will come along with a solution to your problem.

sorry buddy if u have misqouted me ;)

but i think both of just brought me to the right track

---

### Post by joy23 on 2010-02-19
So do mean to say that by trying an always on connection i could access net from both my vista laptop and Xp,linux computer and also connect both with out a problem in LAN?
If yes then i am shifting to it

---

### Post by joy23 on 2010-02-19
> That&#8217;s it you are done ! Now you have always on connection and you do need to click on the desktop dialer ! If you want you can delete the desktop dialer shortcut and also the default dialer for BSNL from the system ! 

After doing this DHCP server will be assigned on ur router & you can connect your wifi devices with default settings. 


the above is from the link 
so does it mean that the dialler is completely useless

---

### Post by joy23 on 2010-02-19
[http://en.kioskea.net/faq/5958-bsnl-...a-a211-1-setup](http://en.kioskea.net/faq/5958-bsnl-...a-a211-1-setup)
from the above link
> That&#8217;s it you are done ! Now you have always on connection and you do need to click on the desktop dialer ! If you want you can delete the desktop dialer shortcut and also the default dialer for BSNL from the system ! 

does it mean the dialer is completely useless?

---

### Post by crazy.nik23 on 2010-03-11
i added a DSL n wrote my username n pass

but when i click on the network tool on the upper right hand side
it says wired network auto eth0 n DSL1 when i click on dsl auto eth0 gets disconnected....
how can i configure...??

---

### Post by joy23 on 2010-04-04
Even i have a kind of critical problem
I can connect to the router and configure it but can't access the internet.
ur present problem and mine is kindof samething

it says connected and after sometime when i click on the dataone connection it disconnects and the again reconnects to if....   connection and says connection established
ip settings are fine now 
i think i am missing something
i don't know what.
Hope someone replies

---

### Post by joy23 on 2010-04-04
i also tried the 
pon dsl-provider   
poff dsl-provider 

.....  described before in the thread
but is says connected but i am not able to view any webpage

---

### Post by dineshs on 2010-04-04
After connecting,open firefox and try this site(type this IP address on the address bar)
64.233.189.104
What do you get?

---

### Post by joy23 on 2010-07-19
if i use the bridge mode 
i can connect to internet
it shows as the google page
but
using the always on mode PPPoE
either the inet lamp will glow or even if it is properly set up i still need a dialer to connect to it
(Above is in windows)
But in linux the story is altogether different
i just can't connect to internet anyhow bridge or pppoe tried both
it either shows as auto eth0 connected or wired network connected but i can't access a webpage
Please can u post me step by step instructions as to how to overcome this and for a wired connection only.
still the kind of problem similar to "crazy.nik23" above.
i can access the modem from linux now properly a huge plus for me now atleaast.
Tried lot of steps but many dont seem to be working.

---

### Post by joy23 on 2010-07-19
Eureka!!!
Eureka!!!
i reset the modem deleted all the entries in wan created it again from starting and now working like charm

It's working
in PPPoE mode in windows
tell me what to do next.
also will this setting be altered if i happen to click on the dialer
but the inet lamp is on too.

---

### Post by joy23 on 2010-07-19
I have asked for a Lucid lnux copy how much time will it take it to reach me
in mumbai ,india?

---

### Post by dineshs on 2010-07-20
If your inet lamp is ON you are in PPPoE mode.You can directly browse the web via firefox in ubuntu.If you have any problem please post back the results of
```
ifconfig -a
```and the contents of
```
gksudo gedit /etc/network/interfaces
```

I think 10.04 DVD is available free with the magazine LINUX FOR YOU june issue

---

### Post by joy23 on 2010-07-21
Sorry yaar it doesn't work!
still bridge works
but as soon as in PPPoE  it has all 3 lights blinking
and no network connectiity got success for the first time but not any more!
Linux still is without internet!.
Any help from anyone would be greatly appreciated.

---

### Post by dineshs on 2010-07-21
What about the command output(in pppoe mode)?
is your internet lamp blinking?
what do you get for(in pppoe mode)```
ping 4.2.2.1
```

---

### Post by greyskulster on 2010-07-21
I recently formatted my laptop and now it has both xp and ubuntu 10.04. I had successfully established bsnl broadband connection in xp,also in ubuntu. It used to be connected without dialling.But now due to some weird happening the network icon has gone from the top panel.To bring it back i accidently messed with the eth0 connection settings and managed to nullify it.Now i cant connect to network from ubuntu.But internet connection is fine in xp.Plz help

---

### Post by dineshs on 2010-07-21
greyskulster,
Pl check
1)system-preferences-startup applications
tick network manager
2)Right click on the top panel-click add to panel-select notification area -click add
If the icon is not back
Please try this
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by greyskulster on 2010-07-21
> **dineshs said:**
> greyskulster,
Pl check
1)system-preferences-startup applications
tick network manager
2)Right click on the top panel-click add to panel-select notification area -click add
If the icon is not back
Please try this
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

thanx for your prompt help...its working...you are a lifesaver :D

---

### Post by dineshs on 2010-07-22
Glad to hear that

---

### Post by joy23 on 2010-07-23
> **dineshs said:**
> What about the command output(in pppoe mode)?
is your internet lamp blinking?
what do you get for(in pppoe mode)```
ping 4.2.2.1
```

yes it blinks not like the dsl one when it is not right slightly different.
but failure after a brief success
i can't connect to internet.
tried with bsnl people but where of no help since they insisted on using XP on bridge mode . such noobs they were!.
You are the only one i depend now!
hope you help.
ping on my xp gives result as 
```

Pinging 4.2.2.1 with 32 bytes of data:

Reply from 4.2.2.1: bytes=32 time=224ms TTL=53
Reply from 4.2.2.1: bytes=32 time=218ms TTL=53
Reply from 4.2.2.1: bytes=32 time=216ms TTL=53
Reply from 4.2.2.1: bytes=32 time=216ms TTL=53

Ping statistics for 4.2.2.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 216ms, Maximum = 224ms, Average = 218ms
```

---

### Post by dineshs on 2010-07-23
> ping on my xp gives result as 
Not in XP.In ubuntu
I am sure the connection will work unless there is some issue with LAN driver.So please do the following (In ubuntu).
step-1
```
gksudo gedit /etc/network/interfaces
```
copy and paste the following [COLOR="Red"](the file should contain only this)[/COLOR]
```
auto lo
iface lo inet loopback

```
save the file and close
step-2
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address [COLOR="Blue"]192.168.1.100 [/COLOR]
mask [COLOR="Blue"]255.255.255.0[/COLOR] 
gateway[COLOR="Blue"] 192.168.1.1 [/COLOR]
[COLOR="Red"]then hit enter [/COLOR]
DNS [COLOR="Blue"]4.2.2.1[/COLOR]
then click apply 
step-3
Restart PC
step-4
If internet is not working,please post the output of
```
ifconfig -a
```
```
ping 192.168.1.1 -c3
```
```
ping 4.2.2.1 -c3
```

---

### Post by joy23 on 2010-07-24
I was placing 208.67.222.222 the open dns one so that was wrong, right?
one problem
the grub has disappeared after i formated one of my drive 
any way to retrieve it?

---

### Post by joy23 on 2010-07-24
```
joy@joy-desktop:~$ gksudo edit gedit /etc/network/interfaces
Warning: unknown mime-type for "/etc/network/interfaces" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
joy@joy-desktop:~$ sudo edit gedit /etc/network/interfaces
Warning: unknown mime-type for "gedit" -- using "application/octet-stream"
Warning: unknown mime-type for "/etc/network/interfaces" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
joy@joy-desktop:~$ 

```

so i tried   cd to network and then   sudo gedit interfaces


```


joy@joy-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:fd:4c:32  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fefd:4c32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6228 (6.2 KB)  TX bytes:7906 (7.9 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

joy@joy-desktop:~$ ping 192.168.1.1 -c3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.930 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.774 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.789 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.774/0.831/0.930/0.070 ms
joy@joy-desktop:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2016ms
, pipe 2


```

even to access my internet in xp i had to revert from pppoe to bridge mode

---

### Post by dineshs on 2010-07-25
> I was placing 208.67.222.222 the open dns one so that was wrong, right?you can use any DNS if you are sure it is working(4.2.2.1 works normally,You can ask BSNL for their DNS servers)
> so i tried cd to network and then sudo gedit interfaces
You were typing```
gksudo [COLOR="Red"]edit[/COLOR] gedit /etc/network/interfaces

```instead of
```
gksudo gedit /etc/network/interfaces
```Try to copy and paste commands> even to access my internet in xp i had to revert from pppoe to bridge mode I understand that the PPPoE software in your modem is not working.May be that is why BSNL is insisting BRIDGE mode
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
> the grub has disappeared after i formated one of my drive 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by joy23 on 2010-07-26
sorry for that silly mistake
tried other but didn't make it
trying bridge on linux hope it works!

---

### Post by joy23 on 2010-07-27
> **joy23 said:**
> sorry for that silly mistake
tried other but didn't make it
trying bridge on linux hope it works!

bridge in linux is working  did something like pppoeconf and minor adjustments in network connections.

so guys any idea about how to get my PPPoE talk?
or is my pppoe real bad?

> I understand that the PPPoE software in your modem is not working.May be that is why BSNL is insisting BRIDGE mode

---

### Post by dineshs on 2010-07-27
Try changing the modem

---

### Post by joy23 on 2011-10-26
Thank you all for all the help !  :popcorn:
all of u showed appreciable patience
sorry for posting so late :(

somewhere it shows to delete all the values there at the start itself and create a new field (VPI 0/ VCI 35)
That's where all the trouble is
instead of deleting it keep everything as it is proceed as posted before and  the router goes into proper pppoe mode with NAT enabled.

"about net remaining always on and my hesitation could be considered as a beginners' hesitance"

no problems whatsoever with that at least especially with  pricey unlimited option.
working fine now.
with pppoe mode inet and ethernet light blinks continuously
both pwr and dsl  are stable.
Finally figured it all out and for a good reason  
thanks (special mention dinesh and mips) :P  :D

---

### Post by joy23 on 2011-11-13
> **dineshs said:**
> Try changing the modem

i dont think that would be necessary now since all started due to a dumb techie telling me to delete all the settings at first.
--------

thumbs up to #20 and #26

now on pppoe always on 

but :cry:  lappie on ventilator now so nothing helpful from it


update --> using 10.04 lucid lynx now

my network icon disappeared and cant see any of my networking devices :confused:

---

### Post by dineshs on 2011-11-14
Pl follow step-1 and 2 [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")

---

### Post by joy23 on 2011-11-14
> **dineshs said:**
> Pl follow step-1 and 2 [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")

I cannot see the network icon so i did something now i can see the icon .
it is not as it was before it lacks eth0 and all other normal views.

I suppose i must have done something to the driver so now ubuntu doesnt detect my lan card at all.
now what?
I think i had updated the driver when it flawed.

realtek RTL 8111/8168 

 i have downloaded the driver now and will let u know if i succeed .
:confused:

---

### Post by joy23 on 2011-11-25
Tried all possible combinations but no effect.
No change
Finally had to do a fresh install.
There was a problem before of packages not installed due to other broken packages never figured that out too!

Finally a fresh install  and a whole night's downloads fixed them all.
Only one remains that to not of linux but of BIOS which hangs as soon as i enter .
Also If i start my router during POST it just Hangs then and there. :confused:](*,):shock::!::frown:

---

