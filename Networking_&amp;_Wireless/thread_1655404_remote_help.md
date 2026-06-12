---
title: "remote help"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by Wickedares on 2010-12-29
i did some searching to see if anyone had posted this somewhere already on this forum but i didn't see anything right away. 

i don't really know what to call what i am wanting to do, and the best thing i can see on the internet searches is, vpn. and i could be wrong at what i gathered vpn to mean. to me vpn sounds like just connecting to a remote desktop to control it via over the internet. please let me know if that is right or wrong.

now i will say what i want ideally to have with my network.

i have a unbuntu machine running with samba setup so that computers in my shop can access the file shares i have on there. now what i need to do now is to be able to access those shares from a completely different network/building through the internet. 

and what im looking for is to log in to the existing network i have established and the solution im avoiding is to be logging in directly to the unbuntu machine since i don't want anyone mess with it. i would like to just be able to from my home in other words log in to the shops network and type in the ip address to my unbuntu machine to see the samba shares and be able to pull them to my home pc or send them back to the unbuntu pc. 

thank you ahead of time.

---

### Post by PatchesTheCaveman on 2010-12-29
If you just need to be able to access files from your Ubuntu machines, theres a much simpler solution than setting up a VPN, which is rather complicated and error-prone, especially with home networks.

Install the Secure Shell Daemon on your Ubuntu by going to Applications > Accessories > Terminal then typing the following command in the black box that appears and pressing Enter:
```
sudo apt-get install ssh
```

If you have a firewall or router between your Ubuntu machine and the Internet, you'll need to open TCP port 22 so you can access it from the Internet.

Then on the Windows computer you want to access the files from, install FileZilla from [http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client).  Once you have it installed, run it and click the leftmost icon on the toolbar in the top left to open the Site Manager.

Click New Site, and pick a name for your connection.  In the Host box, enter your Ubuntu machine's IP address.  Under server type, choose *SFTP - Secure File Transfer Protocol*.  Under Logon Type, select *Normal* to have it remember your username and password or *Ask for password* to have it ask for your password every time you connect.  Enter the username of your Ubuntu account in the Username box, and your normal password in the Password box if you chose to have it remember it.

Click Connect, and you'll instantly have access to folders on your Ubuntu machine and be able to copy them back and forth.  You'll need to enter your password every time if you chose *Ask for password*.  In the future, you can access your server more easily by clicking on the drop-down arrow next to the Site Manager icon and selecting the name you picked earlier.

If you don't want whoever needs to do this to have access to your normal Ubuntu account, create a new account on that machine that only has access to the files and folders they need.  Then use that account in Filezilla.

There's even a way to schedule it so certain folders are copied at the time of your choosing.  I'm not sure how to do that on Windows off the top of my head, so let me know if you want that and I'll look it up.

---

### Post by Wickedares on 2010-12-29
i will for sure try this set up and let you know how it turns out. 

i guess with this method samba is really only used for the lan hear at the shop and wont really have any part in the connecting from home will it? 

thanks for the quick reply also!!!!!

---

### Post by PatchesTheCaveman on 2010-12-29
> **Wickedares said:**
> i guess with this method samba is really only used for the lan hear at the shop and wont really have any part in the connecting from home will it? 

Exactly.  As you noted, using Samba over the Internet requires a VPN, which once again, is complicated and unnecessary for something as simple as file sharing.

My suggestion is very similar to setting up an FTP server (which I noticed you tagged your original post with).  The difference is this method will encrypt your connection so any script kiddie with a packet sniffer won't be able to read your files or passwords over the Internet, like can be done with a regular FTP server.

---

### Post by Wickedares on 2010-12-29
ok so far i have ssh installed on the linux machine and i have a netgear router and i went to the port forwarding section of its setup and forwarded the tcp 22 port i dont know if thats what you intended i dont really have an option to open up a port specificly unless port forwarding means the same thing. and as far as putting in the ip address does it want my local networks ip or another ip and if another ip how do i find out what that would be? 

what i have tried so far is from a windows pc on the same net work so it may be that i will try again on my home pc but filezilla gave me a connection refused error when i tried with the settings i put in.

---

### Post by PatchesTheCaveman on 2010-12-29
Port forwarding is exactly what you want.  Forward TCP port 22 to the local IP address of your Ubuntu machine.

If you just want to test the SFTP connection from another computer on the network, use its local IP address in FileZilla.

If you don't know what that machine's local IP address is, you can figure it out by opening a Terminal on your Ubuntu machine and running the following command:
```
ifconfig
```

Next to one of your interfaces, most likely eth0, one of the lines it spits out looks like this:
```
inet addr:192.168.137.23
```

In this case (my machine) the local IP address is 192.168.137.23.

Note that the *inet addr* next to the interface labeled *lo* is not your local IP address, it is the loopback address, the address that always connects to the machine you're presently on.

When connecting from FileZilla from outside your local network, you'll need the IP address set by your Internet provider.  You can discover this easily by going to [http://www.whatismyip.com/](http://www.whatismyip.com/) in your browser on any computer on the local network.

Note that it is likely your ISP changes your IP address rather frequently.  If you look in your Netgear router settings, there is probably a Dynamic DNS configuration option.  You can set up an account with the site it uses (most likely [http://www.dyndns.com/](http://www.dyndns.com/)) to create a free domain name like wickedares.dyndns.com to use instead of your Internet IP address.  Once you set up an account with DynDNS and input your account information into the Dynamic DNS section of the router configuration, your router will automatically update DynDNS with your IP address when it changes, so wickedares.dyndns.com will always point to the correct IP address.  Then all you have to do is use wickedares.dyndns.com instead of the IP address in FileZilla on the remote computers.

---

### Post by Wickedares on 2010-12-30
i guess my next question is i have the ip from whatismyip.com and put that in and forwareded the port i have tried different usernames and such but i still get connection timed out is there anything i need to do to the linux machine to let it accept a connection?

(edit) i retried it from another computer in the lan and it replyed couldnt connect either replied with erconnection refused and that was using the servers local ip

---

### Post by grahammechanical on 2010-12-30
Don't mind me. I just want to muddy the waters a little bit.

What does Remote desktop do? Does it not give access to a Ubuntu machine over a network (remotely)?

Regards.

---

### Post by Wickedares on 2010-12-30
> **grahammechanical said:**
> Don't mind me. I just want to muddy the waters a little bit.

What does Remote desktop do? Does it not give access to a Ubuntu machine over a network (remotely)?

Regards.

remote desktop in definition is you essentially controlling my desktop from the luxury of your pc and not having to drive to my house to do it.

---

### Post by spiky001 on 2010-12-30
Hi just been through your post, Have you made a connection yet?

---

### Post by Wickedares on 2010-12-30
i have not made contact yet :S lol messed around with fire starter some to see if opening up ssh ports would help and it hasnt and even with that policy off fire starter doesnt pick up on the atack to the computer so im still thinking that its not even getting to the computer yet.

one of my new questions is: that if i find my ip that isp gives me and such i put that in filezilla with the port but how does file zilla know which computer to actualy go to in that ip address'es network? i would have figured there would be an area for lan ip also

---

### Post by spiky001 on 2010-12-30
Ok are you at home away from pc on internet, Or in office on local network. The machine you wish to connect to is ubuntu (host)? What is the machine you are using (client) windows or ubuntu?

---

### Post by PatchesTheCaveman on 2010-12-30
Okay let's start with the simple things.  From the Ubuntu machine, go to Applications > Accessories > Terminal.

Then run:
```
ssh localhost
```

It will prompt you to accept the key fingerprint of your local machine.  Say yes.  It should then ask you for your password.  If it does all that, you know the SSH daemon is working.  If you get an error, let me know.  Something is seriously wrong.

If that's working, than you might be running some sort of firewall on the Ubuntu machine that's blocking port 22.  Go to System > Administration and look for a program called "Firestarter" or any other sort of firewall software.  If you find something, open port 22.

If you're still having trouble, download PuTTY from [http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe) on the Windows computer on your LAN and run it.  Enter your Ubuntu machine's local IP address in the Host Name.  Leave everything else alone and click Open.  That should prompt you to accept the Ubuntu machine's encryption key and log in to the Linux terminal on that machine.  If that works, give FileZilla a try again.  Make sure all the settings match exactly what you tried in PuTTY.

If it's still not working, go to Start (and Run on Windows XP or type in the search box on Vista/7) and type cmd and press Enter.  Type ping and a space and the local IP address of your Ubuntu machine.  If it times out and shows 100% packet loss, you might have the wrong IP address.  Double-check *ifconfig*.  You might be able to figure it out from your router configuration as well.

---

### Post by Wickedares on 2010-12-30
> **spiky001 said:**
> Ok are you at home away from pc on internet, Or in office on local network. The machine you wish to connect to is ubuntu (host)? What is the machine you are using (client) windows or ubuntu?

as i type i have a laptop with win7 connected via verizon to test this beast out with

 but in the long run it will be a windows pc connecting to the ubuntu machine from a different network.

---

### Post by PatchesTheCaveman on 2010-12-30
> **Wickedares said:**
> one of my new questions is: that if i find my ip that isp gives me and such i put that in filezilla with the port but how does file zilla know which computer to actualy go to in that ip address'es network? i would have figured there would be an area for lan ip also

That's what port forwarding on the NETGEAR router does, but if you can't even connect using the local IP address from another computer on your LAN, something else is awry.  Once you get a connection working across your LAN, you can take a screenshot of your port forwarding screen so I can tell you if it's set up correctly, if you would like.  :-)

---

### Post by PatchesTheCaveman on 2010-12-30
In Firestarter, you want to have a rule allowing all traffic for SSH, like in the first screenshot.

I usually allow all traffic from my local network too, as in the second screenshot.  If IP addresses on your local network are 192.168.1.1, 192.168.1.2, 192.168.1.100, etc., enter "192.168.1.0/24".  Adjust as necessary if you use a different set of IP addresses.

---

### Post by Wickedares on 2010-12-30
ok putty worked from a local windows machine
(edit) and that was with firestarter  dissabled  so local network works even without firestarter 

still no luck on filezilla

---

### Post by Wickedares on 2010-12-30
i dont guess it maters that i have my laptop im testing this filezilla with connected via teather to my phone. it has never blocked any connections like this before but i have never tried ssh though i will for sure try it once i get to my home pc tonight and see if it works there.

---

### Post by spiky001 on 2010-12-30
How i use Filezilla through ssh is Filezila then File site manager then I set the SERVERTYPE to SFTP this is the settings I use see screen shot

---

### Post by PatchesTheCaveman on 2010-12-30
Yes, you should have it set to "SFTP - Secure File Transfer Protocol" like spiky001, but leave the port at the default setting:  22.

You can try FileZilla from a local machine but if PuTTY worked I'm sure it will.

If you can, take a screenshot (with the PrntScrn key) of your Port Forwarding settings in your NETGEAR router configuration.  I'm pretty sure that's where the hangup is.

Also make sure you're using your network's public IP address (from WhatIsMyIP) not your local address when trying to connect through the Verizon connection.

---

### Post by Wickedares on 2010-12-30
filezilla worked from lan computer to ubuntu computer here is my port forwarding

---

### Post by spiky001 on 2010-12-30
So do you know the external IP address

---

### Post by Wickedares on 2010-12-30
yes i do know external ip from whatismyip.com

and i put that in host area of filezilla and put the port in and also my user and pass word that worked in the lan still no luck

i tried a ssh app off of android market on my phone and it didnt connect either

---

### Post by Wickedares on 2010-12-30
i dont know if it helps or not im getting a connection time out, could not connect to server on filezilla

---

### Post by PatchesTheCaveman on 2010-12-30
That all looks good.  It's possible your ISP is doing some port blocking.

From a computer on your local network, go to the ShieldsUP! firewall testing tool at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Click Proceed.  Enter 22 in the text box in the blue box toward the bottom.  Click "User Specified Port Probe".  Does it report port 22 as open, closed, or stealth?

---

### Post by spiky001 on 2010-12-30
You could try with this [http://nmap-online.com/](http://nmap-online.com/)  If you select custom scan replace the -F with -p 22 (port number 22) if that is the port you have set, That will tell you port 22 is visible to internet + your ip

---

### Post by Wickedares on 2010-12-30
> **PatchesTheCaveman said:**
> That all looks good.  It's possible your ISP is doing some port blocking.

From a computer on your local network, go to the ShieldsUP! firewall testing tool at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Click Proceed.  Enter 22 in the text box in the blue box toward the bottom.  Click "User Specified Port Probe".  Does it report port 22 as open, closed, or stealth?
k that showed 22 as stealthed :S so how do i change that?

---

### Post by PatchesTheCaveman on 2010-12-30
Change the Start Port in your port forwarding settings to something high, like say 24000.  Leave the End Port at 22.  Then plug that in to the port box next to your IP address in FileZilla.

---

### Post by Wickedares on 2010-12-30
> **PatchesTheCaveman said:**
> Change the Start Port in your port forwarding settings to something high, like say 24000.  Leave the End Port at 22.  Then plug that in to the port box next to your IP address in FileZilla.
ok well that first line of code is not working i can go and find the file and open and look at it and see where your talking about and i didnt know if i did the chown command on the file and change the user if that would mess anything up?

---

### Post by Wickedares on 2010-12-30
netgear wont let me make a start port a bigger number than the ending one i guess :S

---

### Post by PatchesTheCaveman on 2010-12-30
That's annoying.  We'll have to go with my first solution then.

Run this command:
```
gksudo gedit /etc/ssh/ssh_config
```

In that file, find the line that says:
```
#     Port 22
```

Delete the hash mark and change the port to something high like 24000 so it says:
```
    Port 24000
```

Save and exit.  Then, restart the SSH daemon by running:
```
sudo service ssh restart
```

Give it a quick test by running:
```
ssh -p 24000 localhost
```
If you can enter your password, you should be good.

Now, go into firestarter if you haven't disabled it and add a rule allowing port 24000 or whatever you used.  Then go into your router config and change the start and end ports to 24000.

Finally, change the port in FileZilla next to your IP address to 24000 and give it a try.

---

### Post by Wickedares on 2010-12-30
> **PatchesTheCaveman said:**
> That's annoying.  We'll have to go with my first solution then.

Run this command:
```
gksudo gedit /etc/ssh/ssh_config
```

In that file, find the line that says:
```
#     Port 22
```

Delete the hash mark and change the port to something high like 24000 so it says:
```
    Port 24000
```

Save and exit.  Then, restart the SSH daemon by running:
```
sudo service ssh restart
```

Give it a quick test by running:
```
ssh -p 24000 localhost
```
If you can enter your password, you should be good.

Now, go into firestarter if you haven't disabled it and add a rule allowing port 24000 or whatever you used.  Then go into your router config and change the start and end ports to 24000.

Finally, change the port in FileZilla next to your IP address to 24000 and give it a try.
says gtk-warning**: cannot open display: 

when i type in that first line of code

---

### Post by PatchesTheCaveman on 2010-12-30
> **Wickedares said:**
> says gtk-warning**: cannot open display: 

when i type in that first line of code

That's very strange.  Are you on a completely text console instead of a terminal window in GNOME?

At any rate, run this command instead:
```
sudoedit /etc/ssh/ssh_config
```

That will use nano, a console editor instead of the GNOME graphical editor.

Edit the file, and when you are done, press CTRL+X to exit the editor.  Press *y* when you're asked if you want to save.

---

### Post by Wickedares on 2010-12-30
this may sound dumb but it opens up in my terminal and i have options after i edit it at the bottom of my screen i see a write out option which i found out you have to press ctrl+o to do that but it doesnt seem to save the text when i go to read the file again its the same way it was

---

### Post by Wickedares on 2010-12-30
<-------------- dummy for not reading all the way through your post where you explain how to save it lol

---

### Post by Wickedares on 2010-12-30
ok so editied it and used the command for the sudo service ssh restart and it said ssh start/running, process 22792 

but when i run the ssh -p 24000 localhost says connection refused

---

### Post by spiky001 on 2010-12-30
try ssh -p 24000 user@ipaddress

---

### Post by Wickedares on 2010-12-30
> **spiky001 said:**
> try ssh -p 24000 user@ipaddress
that came up "bad port" using my username@localip

---

### Post by PatchesTheCaveman on 2010-12-30
Try:
```
sudo service ssh stop
sudo service ssh start
ssh -p 24000 localhost
```

If it still doesn't work, run:
```
cat /etc/ssh/ssh_config
``` and copy and paste here.


> try ssh -p 24000 user@ipaddress
By default it uses your current username to try and connect so you don't need the *user@* when you're on the same machine.

---

### Post by spiky001 on 2010-12-30
Is the Firewall blocking it?

---

### Post by PatchesTheCaveman on 2010-12-30
> **spiky001 said:**
> Is the Firewall blocking it?

He was trying it locally on the same machine.  The firewall shouldn't touch the loopback device.

---

### Post by msandoy on 2010-12-30
Ithink OP needs to start over from beginning with the port config. Configure ssh_server to listen to port 22, make correct port forwarding in router of 22 to correct IP. Install nmap on separate computer and do "nmap internalIP of server" and "nmap externalIP", and post results. This will tell you if the router is causing this problem, or if it is the frewall on your ubuntu server.
It also might help if you try
```

sudo ufw disable

```
and then do another connection test on the external IP.

---

### Post by Wickedares on 2010-12-30
> **msandoy said:**
> Ithink OP needs to start over from beginning with the port config. Configure ssh_server to listen to port 22, make correct port forwarding in router of 22 to correct IP. Install nmap on separate computer and do "nmap internalIP of server" and "nmap externalIP", and post results. This will tell you if the router is causing this problem, or if it is the frewall on your ubuntu server.
It also might help if you try
```

sudo ufw disable

```
and then do another connection test on the external IP.

see the problem is though bellsouth seems to be hiding the 22 port cause a website told me it was stealth on my ip.

---

### Post by PatchesTheCaveman on 2010-12-30
Actually it could also say Stealth if the firewall was blocking it.

Open a terminal and run:
```
cat /etc/ssh/ssh_config
```
and copy and paste here so I can see where you're at and we'll go from there.

---

### Post by msandoy on 2010-12-30
> **Wickedares said:**
> see the problem is though bellsouth seems to be hiding the 22 port cause a website told me it was stealth on my ip.

Well, then you can always use port 443, they will not close that one. It is normally for https traffic. And there was no mention of a web server in the setup here.

---

### Post by Wickedares on 2010-12-30
> **PatchesTheCaveman said:**
> Actually it could also say Stealth if the firewall was blocking it.

Open a terminal and run:
```
cat /etc/ssh/ssh_config
```and copy and paste here so I can see where you're at and we'll go from there.


# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 24000
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

---

### Post by PatchesTheCaveman on 2010-12-30
Okay cool, your ssh is still on port 22 because you didn't remove the **#**.  We'll leave it that way for now.  From what I can tell, BellSouth does **not** block port 22, so it was probably your firewall getting in the way.

Run this in a terminal to disable your firewall for now:
```
sudo ufw disable
```

Then go back to your router configuration and switch it back to port 22 start and end if it's not that way already.

After that, go back to [http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2) and test port 22 again.

If it says open, give FileZilla a shot from your Verizon laptop again.  But let me know if it still says Stealth.

---

### Post by Wickedares on 2010-12-31
> **PatchesTheCaveman said:**
> Okay cool, your ssh is still on port 22 because you didn't remove the **#**.  We'll leave it that way for now.  From what I can tell, BellSouth does **not** block port 22, so it was probably your firewall getting in the way.

Run this in a terminal to disable your firewall for now:
```
sudo ufw disable
```

Then go back to your router configuration and switch it back to port 22 start and end if it's not that way already.

After that, go back to [http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2) and test port 22 again.

If it says open, give FileZilla a shot from your Verizon laptop again.  But let me know if it still says Stealth.

nope still showing up as stealth
:S

---

### Post by PatchesTheCaveman on 2010-12-31
That's irritating.  Let's do a quick test to see if it's Ubuntu or the router that's the problem.  Plug your Ubuntu machine directly into your DSL modem, if possible.  Then try FileZilla one more time.

Also, make sure your IP address has not changed in the interim.  Some ISPs change their customer's IP address quite frequently.

---

### Post by Wickedares on 2010-12-31
> **PatchesTheCaveman said:**
> That's irritating.  Let's do a quick test to see if it's Ubuntu or the router that's the problem.  Plug your Ubuntu machine directly into your DSL modem, if possible.  Then try FileZilla one more time.

Also, make sure your IP address has not changed in the interim.  Some ISPs change their customer's IP address quite frequently.

I will have to try that tomorrow when I go back to work.......  once again thank everyone for your ideas and help!

---

### Post by msandoy on 2010-12-31
I encountered a similar case a few days ago, the OP in that case did not know how port forwarding worked, and just entered an available IP adress (Not taken by any computer on the network) for the forwarded port. Leaving all traffic going into the bit bucket.
OP: Make sure the port forwarding in the router is set to the internal IP address of your Ubuntu computer.

---

### Post by Wickedares on 2010-12-31
i promise i have the same local ip atatched to the port forward.

i still hadnt got to swap my computer directly to modem yet i will post results once i do.

---

### Post by PatchesTheCaveman on 2010-12-31
He even posted the firewall config screenshot so we could check and he could SSH to it on the local network so I'm pretty sure he got that right.

Make sure you turn off the firewall on the Ubuntu box again when you try because it will turn back on when you reboot:
```
sudo ufw disable
```

---

### Post by Wickedares on 2010-12-31
> **PatchesTheCaveman said:**
> He even posted the firewall config screenshot so we could check and he could SSH to it on the local network so I'm pretty sure he got that right.

Make sure you turn off the firewall on the Ubuntu box again when you try because it will turn back on when you reboot:
```
sudo ufw disable
```
ok server direct to the modem did not work i reran the sudo ufw diable befor hand and also checked the external ip to make sure that didnt change and still no luck :S

---

### Post by PatchesTheCaveman on 2010-12-31
Maybe they are blocking your port then.  All the Googling I did didn't reveal any BellSouth customers having trouble doing SSH though.

Run ```
sudoedit /etc/ssh/ssh_config
``` again and change the port to something high like 24000.  Remember to delete the # (pound sign) at the beginning of the line this time.

Run ```
sudo service ssh restart
``` to switch the running SSH daemon to the new port.  Then run ```
ssh -p 24000 localhost
``` to test and see if the new ports working.

Leave your firewall disabled and try a direct connection without the router again if possible.  Remember to change the port in the FileZilla site manager.  If you can't do it directly this time or that works, remember to change the router port forwarding settings too.

---

### Post by Wickedares on 2010-12-31
well i left a little while ago i will try that direct with those port settings again monday and let you know what happens

---

### Post by Wickedares on 2011-01-05
ok so i have some news to update you all on i found out that my modem was still reciveing the incoming ip and worrking as a router also. but my boss wants to ddo the vpn set up and we already bought a buffalo router that has a vpn server built in to it i used a vpn walkthrough on  one of their stickys  in the buffalo forums still no luck unfortuneletly i even retried the ssh with port forwarding on the new router and thats still not working either

---

