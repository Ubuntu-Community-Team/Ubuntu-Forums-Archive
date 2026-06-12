---
title: "force new ip with DHCP without reboot?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by trek7 on 2009-05-18
How do I in Ubuntu (or even better, on many different Linux varieties) force a new ip on a computer with DHCP without rebooting. On a Windows XP system these steps successfully changes the ip for a computer for my ISP:
```
ipconfig /release
net stop DHCP
net start DHCP
ipconfig /renew
```
Can someone please post something equivalent for Ubuntu.
 
Here are some things I've found by searching that didn't work:
```
sudo ifdown eth0
sudo ifup eth0
```
 
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
 
```
 
sudo dhclient -r
sudo dhclient

```

---

### Post by Jose Catre-Vandis on 2009-05-18
Do you mean you got the same IP address again? You router is responsible for that, not your PC?

---

### Post by Jive Turkey on 2009-05-18
to get a new IP from your ISP or your own router?  I found a handy trick to get a new IP assigned to my cable modem from my ISP.  If that's what you need pm me.  I wont go to the trouble to post it here since it may not reflect your actual config, or your aim.

---

### Post by trek7 on 2009-05-19
What router? :) The computer is not connected through a router and so gets a "real" ip from the ISP, not an internal 169... ip. As I described, the first quoted commands above is enough in Windows XP to force a new ip adress onto the computer in a matter of seconds. I want to reproduce exactly that in Ubuntu. The above mentioned linux commands does not work. I get the same ip over and over again.

---

### Post by mtron on 2009-05-19
well, i guess that your isp assigns the same ip as before because the same mac address requested it. 

Change the mac address in Network manager (Look for the Connection panel icon, right click - Edit Connections - Wired Connection tab - select auto eth0 and click the edit button). Network Manager should automatically request a new ip from your ISP's DHCP server.

if you don't use a X-display or Network-Manager do;

```
sudo ifdown eth0
sudo gedit /etc/network/interfaces
```

look for the stanza

```
auto eth0
iface eth0 inet dhcp
```

and add the hwaddress line as shown below ( you might want to use a similar mac as before and just change e.g. the last digit)

```
auto eth0
iface eth0 inet dhcp
    hwaddress ether A1:B2:C3:D4:E5:F6
```

and now bring up the interface (sudo ifup eth0) and see if you got another IP.

---

### Post by Jose Catre-Vandis on 2009-05-19
> **trek7 said:**
> What router? :) The computer is not connected through a router and so gets a "real" ip from the ISP, not an internal 169... ip. As I described, the first quoted commands above is enough in Windows XP to force a new ip adress onto the computer in a matter of seconds. I want to reproduce exactly that in Ubuntu. The above mentioned linux commands does not work. I get the same ip over and over again.

Your ISP is still using a router, just that you can't manage its behaviour. mtron seems to be on the right lines :)

---

### Post by trek7 on 2009-05-19
The above working solution for Windows XP is a .bat script. I only need to run it and then get a new ip without any manual steps. I seek a similarly automated solution for Ubuntu. So manually going via Network Manager is out. 
 
The commands mtron posted might've been possible to put together into a single script. But they didn't work on my system -- the ip didn't change. I also wonder why there's a need to change the MAC adress. The Windows XP way of forcing an ip change does not seem to involve changing the MAC adress -- why then do that in Ubuntu? I'm asking since to be able to do what you suggest repeatedly I would need a more complex script that autogenerates unique but valid MAC adresses. Isn't there some easier solution?

---

### Post by trek7 on 2009-05-21
I just spent 30 minutes searching even more for a solution for this. I'm confident that there MUST be a very easy way to achieve what I want, I just can't find out what it is. Very annoying! Is there really no one around that knows the ins and outs of DHCP networking in Ubuntu enough to solve this little issue?

---

### Post by Jose Catre-Vandis on 2009-05-21
A different IP address is dependent on the setup of the router issuing them. Even your ISP would wish to reduce network load to avoid having to issue new IP adresses to the same MAc address again and again.

Have a look at these two conflicting websites

[http://www.trap17.com/index.php/Ip-Address_t46701.html](http://www.trap17.com/index.php/Ip-Address_t46701.html)

[http://www.novell.com/coolsolutions/trench/16013.html](http://www.novell.com/coolsolutions/trench/16013.html)

We are getting to the point of wondering what is wrong with the IP address you are getting?

The only way I can see is to:

```
sudo dhclient -r
sudo dhclient
```
but because you cannot control what your ISPs router is doing, it is most likley to lease you the same IP addy back again. Only by spoofing your MAC address do you have a chance of working round this. A simple bash script should do this all for you.

---

### Post by trek7 on 2009-05-21
[LEFT]Please do not open a discussion about reasons for forcing a change of the ip. That is not relevant to the question. I request that we take the question as given.[/LEFT]
 
> **Jose Catre-Vandis said:**
> Only by spoofing your MAC address do you have a chance of working round this. A simple bash script should do this all for you.
 
It is true that I cannot directly control what the ISPs router is doing. That is true also when using Windows XP. When Windows XP runs the .bat script detailed above the computer sets itself in such a mode that the ISPs router in this case reacts by granting a new ip. This does NOT as far as I can see involve Windows XP spoofing a new MAC adress for the NIC.
 
I don't understand why spoofing the MAC adress would then be necessary in Ubuntu.
 
But if it was then I don't know enough bash to be able to write a single script that has the features already described that on each run generates a valid but different MAC adresses which in turn leads to a new ip adress. If it is simple, can you or someone else help me out in writing that script as a whole?

---

### Post by trek7 on 2009-05-21
I may have found a solution now! I tried it successfully on a machine with Xubuntu right now but chances are this will work in Ubuntu too: 
```
 
sudo dhclient -r
sudo rm /var/lib/dhcp3/dhclient.leases
sudo dhclient

```
 
The second row deletes the leases database (which contains information about the last used ip). That seems to do the trick.
 
(more info on the leases database here: [http://linux.about.com/library/cmd/blcmdl8_dhclient.htm](http://linux.about.com/library/cmd/blcmdl8_dhclient.htm) )
 
My hunch that the solution would be simple and NOT involve MAC spoofing was correct -- I am glad that I persisted with it! :D

---

### Post by Jose Catre-Vandis on 2009-05-21
Hmmm

On my xubuntu 9.04 the info is held in
```
/var/lib/dhcp3/dhclient-eth0.lease
```
so check the files first

My enquiry about the reason  / need was simply in hope that this may point to an alternate solution, and not intended to offend :)

Another suggestion might be if your ISP offers more than one DNS server would be to select the secondary as primary, the dhcp servers might be issuing IP addresses in different ranges?

Please advise if your solution worked...

---

### Post by trek7 on 2009-05-21
Tried it now and it works! :) Thanks for the replies!
 
I also have this file: dhclient-eth0.leases 
But removing only dhclient.leases is enough on the systems I've tried. So I'm leaving that other file as is for now.
 
Here are all the steps I did to be able to run the "force ip change script" without having to enter a password each time: 
 
1. create new file [scriptname.sh] in a folder
2. in a terminal window: sudo chmod +x [path]/[scriptname.sh]
(that makes the file executable)
3. in a terminal window: sudo visudo
4. add a line with this format at the end of the file:
[username] ALL=(ALL) NOPASSWD: [path]/[scriptname.sh]
5. save: ctrl+o , change filename to "sudoer" (not "sudoer.tmp"), enter, Y to confirm save
 
6. run the script each time you want to change the ip
 
(I'm writing these steps in case someone who finds this topic through search also want to setup the script like that. Note that the script works only if the computer connects directly to the ISP. It won't work if there's a "consumer hardware router" inbetween the computer and the ISP. And I guess it won't work at all for some ISPs either.)

---

### Post by Glace on 2009-07-14
Thank you! Very useful!

---

### Post by lotuseclat79 on 2009-07-30
Hi trek7,

I have just been looking at the same issue and discovered the file mentioned by Jose, i.e. /var/lib/dhcp3/dhclient-eth0.lease.  As it so happens, my ISP has an excellent CD PDF document on configuring the router supplied by the ISP or even changing to another router.  They recommend using the pump command to acquire a new ip address.

If you look inside the .lease file, you should find a line such as:
option dhcp-lease-time 86400;
which seems to indicate that by default, the lease lasts exactly 1 day (86400 seconds).  Editing this file should also work to acquire a new ip address by changing the lease time.

As I understand the .lease file, if you release the lease, and then make a new request for a lease, you should be able to get a new ip address from your ISP.

One way I detect my router's ip address is to use the Firefox add-on, "Show MyIP" which encodes a call to a web site in Germany (add-on's author web site) via javascript from a .jar file in the chrome directory of the Firefox extension for "Show MyIP", and that interaction returns the current ip address, unless you are using a proxy like Tor, in which case you would get the ip address for the exit node (3rd hop in Tor network).

You can acquire the pump command from the repositories, and install it for Jaunty.  Then you can look at the man page for the pump command.

I think if you go through the procedure I am recommending, you will be using a very solid technique rather than just deleting the .lease or .leases file(s) which does work, but is somewhat ill-informed about the correct procedure (there always is one) to do the action of getting a new ip address after tossing the current one by releasing it.

-- Tom


> **trek7 said:**
> Tried it now and it works! :) Thanks for the replies!
 
I also have this file: dhclient-eth0.leases 
But removing only dhclient.leases is enough on the systems I've tried. So I'm leaving that other file as is for now.
 
Here are all the steps I did to be able to run the "force ip change script" without having to enter a password each time: 
 
1. create new file [scriptname.sh] in a folder
2. in a terminal window: sudo chmod +x [path]/[scriptname.sh]
(that makes the file executable)
3. in a terminal window: sudo visudo
4. add a line with this format at the end of the file:
[username] ALL=(ALL) NOPASSWD: [path]/[scriptname.sh]
5. save: ctrl+o , change filename to "sudoer" (not "sudoer.tmp"), enter, Y to confirm save
 
6. run the script each time you want to change the ip
 
(I'm writing these steps in case someone who finds this topic through search also want to setup the script like that. Note that the script works only if the computer connects directly to the ISP. It won't work if there's a "consumer hardware router" inbetween the computer and the ISP. And I guess it won't work at all for some ISPs either.)

---

