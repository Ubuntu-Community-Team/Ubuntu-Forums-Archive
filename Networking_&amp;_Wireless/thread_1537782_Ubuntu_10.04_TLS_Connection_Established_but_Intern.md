---
title: "Ubuntu 10.04 TLS Connection Established but Internet not working"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by naveen9885 on 2010-07-24
My wired network dead which i used before 1hr. I seen my firestar firewall application blocked a hit from my internet provider gateway address. I allowed all the connection from my provider gateway after that hit. It did not work. I installed a new OS ubuntu 10.04 tls. and assigned the IP address but still I cant acess the internet. It says connection was established but i cant browse net. Some one pls help me. I tried configuring fire fox. no use.I am using Internet dish. I configure it by browser by entering dish IP.

---

### Post by naveen9885 on 2010-07-24
My wired network dead which i used before 1hr. I seen my firestar  firewall application blocked a hit from my internet provider gateway  address. I allowed all the connection from my provider gateway after  that hit. It did not work. I installed a new OS ubuntu 10.04 tls. and  assigned the IP address but still I cant acess the internet. It says  connection was established but i cant browse net. Some one pls help me.

---

### Post by naveen9885 on 2010-07-24
My wired network dead which i used before 1hr. I seen my firestar  firewall application blocked a hit from my internet provider gateway  address. I allowed all the connection from my provider gateway after  that hit. It did not work. I installed a new OS ubuntu 10.04 tls. and  assigned the IP address but still I cant acess the internet. It says  connection was established but i cant browse net. Some one pls help me.

---

### Post by naveen9885 on 2010-07-24
My wired network dead which i used before 1hr. I seen my firestar  firewall application blocked a hit from my internet provider gateway  address. I allowed all the connection from my provider gateway after  that hit. It did not work. I installed a new OS ubuntu 10.04 tls. and  assigned the IP address but still I cant acess the internet. It says  connection was established but i cant browse net. Some one pls help me. I tried configuring fire fox. no use.I am using Internet dish. I configure it by browser by entering dish IP.  I tried configuring fire fox. no use.I am using Internet dish. I configure it by browser by entering dish IP.

---

### Post by AfrikaDietmar on 2010-07-24
How do you connect to the web ? With a Modem/Router ? Is it DHCP enabled ?

Switch off Firestarter, and then try to surf the web, does it work ?
Other option, uninstall Firestarter and use this as Firewall: Gufw 10.04.5, install it from the Ubuntu Software Centre.

---

### Post by naveen9885 on 2010-07-24
Thanks for the quick reply. I am using  Dish for my internet. And as I said I removed the old one and installed the fresh os in which I did not install anything. I just entered IP address details. and tried browsing. It says connectiion established but not able to browse the net not even install softwares from ubuntu center.

---

### Post by AfrikaDietmar on 2010-07-24
i have no idea how a dish works, do you enter an ip address in your browser to access it and to configure it ? 

Do you see if DHCP is enabled ?

When you are connected, in your tab, you see those 2 arrows, one goes up and one goes down, when you right click on it, go on edit connections, > then go on your connection, go on edit:

we can try the following and see if it works:
Leave MAC address empty
Put MTU on automatic
On tab: 802.1x Security, just leave it, click nothing active there
On tab: IPv4, set Method on Automatic DHCP (if question above is yes)
On tab: IPv6, set Method on Ignore

Disconnect, reconnect, and see if it works.

---

### Post by naveen9885 on 2010-07-24
ya  I configure it by device ip address in the browser.But we dont need to configure every time its a one time configuration process.

---

### Post by AfrikaDietmar on 2010-07-24
ok.

so is DHCP enabled in your dish settings ?

I didn't mean to re configure your dish, but your connection details in your ubuntu operating system by right clicking here, check screenshot. I've attached it with this post.
Then follow instructions above and let me know if it works.

---

### Post by naveen9885 on 2010-07-24
ya its perfect there. Dont have any problem with connection. it says connection established.

---

### Post by AfrikaDietmar on 2010-07-24
connection established is 1 part.
Now you will need to check the settings so that you can surf the web...

right click on those 2 arrows as i have shown you in the screenshot and do this:
 
> then go on your connection, go on edit:

we can try the following and see if it works:
Leave MAC address empty
Put MTU on automatic
On tab: 802.1x Security, just leave it, click nothing active there
On tab: IPv4, set Method on Automatic DHCP (if question above is yes)
On tab: IPv6, set Method on Ignore

Disconnect, reconnect, and see if it works.

---

### Post by naveen9885 on 2010-07-24
Done no use.

---

### Post by naveen9885 on 2010-07-24
do u have solution for this.

---

### Post by Iowan on 2010-07-24
From Code of Conduct:> 
# Please do not cross post, or post the same thing in multiple locations. I've merged/moved/deleted the four copies of your first post to this thread.

---

### Post by naveen9885 on 2010-07-24
Ok but can u help me with this issue.

---

### Post by gordintoronto on 2010-07-24
What do you mean by "dish"?

Is it possible this is a DNS issue?  What do you get from:
cat /etc/resolv.conf

---

### Post by naveen9885 on 2010-07-25
A wireless router is placed on top of my house from there I will be connected to laptop  through cable. It showed my Ip.


[IMG]http://i25.tinypic.com/2uypv1f.png[/IMG]

---

### Post by naveen9885 on 2010-07-28
Some help me pls. I am missing ubuntu a lot.

---

### Post by ubunterooster on 2010-07-28
"connection established" means your computer is connected to the *router*. Can you access the router settings by entering 192.168.2.1 (it might be 192.168.1.1 but I think it is most likely to the first) into the firefox address-bar. See if the *router* is connected to the internet. Are there any other computers using this router to connect?

It is past 1:00AM so I need to go to bed and cannot help you tonight.

---

### Post by dineshs on 2010-07-28
please post the results of
```
ifconfig -a
```and ```
ping 4.2.2.1 -c3
```

---

### Post by naveen9885 on 2010-07-28
My router Ip was changed by provider I will ask him and let u know ubunterooster and dineshs here is the pic.

[IMG]http://i27.tinypic.com/vfdx95.png[/IMG]

---

### Post by dineshs on 2010-07-29
You are getting reply from open DNS 4.2.2.1(so you are connected to internet)> **naveen9885 said:**
>  I just entered IP address details. and tried browsing. It says connectiion established but not able to browse the net not even install softwares from ubuntu center.
Where did you enter the IP details?Network manager or /etc/network/interfaces?
If you are using NM Please try this
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit
select ipv4 
method-manual 
click add 
address ,mask  and gateway you have already entered 
make DNS as  [COLOR="Blue"]4.2.2.1[/COLOR]
then click apply
Any improvement?

---

### Post by naveen9885 on 2010-07-29
Excellent you are great dineshs. My issue was resolved. I can browse the Internet. now. If u don't mind can u please tell me what exactly happened here and what r the steps should be taken now. I mean can I use that DNS address 4.2.2.1  address I am new to Ubuntu.pls suggest me and give me the information

---

### Post by dineshs on 2010-07-29
[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)
4.2.2.1 is an open DNS server.If you  assign default gateway IP as DNS you must be sure that the DNS server addresses available in the router/modem are working.You can use the following DNS addresses if your ISP maintained DNS servers are down
4.2.2.1
8.8.8.8
8.8.4.4

---

### Post by naveen9885 on 2010-07-29
huum I did not get u and i don't know how to check that one also.. will i have any problem if I use this open DNS server means possibility of hacking or some other attacks. And pls suggest me the best firewall to.. And one more thing by using the same router same settings and DNS address not open one. I can browse Internet on windows . But not in Ubuntu.why it happening like that.

---

### Post by dineshs on 2010-07-29
I use open DNs and no firewall.I have heard of firestarter which you can try.You can install it via synaptic package manager or via commandline
```
sudo apt-get install firestarter
```
> I can browse Internet on windows 
The same DNS set there will work in ubuntu

---

### Post by naveen9885 on 2010-07-29
Hi Dinesh.one last question should we install firewall and anti-virus for Ubuntu 10.04  TLS.. Is Ubuntu 10.04 TLS completely safe with out firewall and anti-virus

---

### Post by dineshs on 2010-07-29
I have been using ubuntu for last 3 years without firewall and antivirus -No problem yet.I do not know whether these are essential.clamav,AVG linux version etc are available,but I think(I am not sure) they are used for treating windows viruses as linux is a carrier(ie if a thumbdrive has virus it cant affect linux but may get copied)

---

### Post by naveen9885 on 2010-07-29
Dinesh Thanks for being patience and answering to my questions. And a BIG thanks for resolving issue. Thanks a lot for that. Have a Nice Day.

---

### Post by dineshs on 2010-07-29
Happy to hear that.Welcome

---

### Post by buddhasurf on 2010-08-04
> **dineshs said:**
> You are getting reply from open DNS 4.2.2.1(so you are connected to internet)
Where did you enter the IP details?Network manager or /etc/network/interfaces?
If you are using NM Please try this
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit
select ipv4 
method-manual 
click add 
address ,mask  and gateway you have already entered 
make DNS as  [COLOR=Blue]4.2.2.1[/COLOR]
then click apply
Any improvement?

I am having the same problem. Where can I find the gateway to enter? Also, when I enter the Ping 4.2.2.1 -c3 , it says that the network is unreachable.

---

### Post by dineshs on 2010-08-05
> Also, when I enter the Ping 4.2.2.1 -c3 , it says that the network is unreachable.
1)What connection are you using?DSL or dialup?
2)If DSL,How is your modem configured ?PPPoE or Bridge?
3)post the output of ```
ifconfig -a
```
4)It is better to start a new thread
5)> I am having the same problem. Where can I find the gateway to enter?
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by cnu1 on 2010-10-23
If you have "connection established" but still unable to use Internet, try this [I did and it worked]:

*  Reboot Ubuntu and let it come to the "connection established" stage
*  No disconnect it
*  Click on the network icon and see if your laptop is able to see your router
*  If it can see [it should because you said you have "connection established" earlier] try reconnecting again


I have tried changing all settings in ipv4 and router settings, resolv.conf, grub nothing worked.  That simple above thing was sufficient! [God learning simple lessons hard way]

---

### Post by roshanbernard on 2011-11-10
Hi dinesh..

u are awesome...i had connection no browse issue...as per ur suggestion i used open DNS server...thanks a lot mate..:-)

---

