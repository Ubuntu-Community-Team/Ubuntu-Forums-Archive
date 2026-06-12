---
title: "Getting Through the Trials of Networking With Others"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by oldefoxx on 2010-02-12
I once knew a guy that was into handwriting analysis.  You see or hear about it sometimes, where how you write is suppose to say something about your personality.  So he asked me for a sample of my handwriting to see what he could determine about my personality from it.  I wrote out a page of my thoughts (I never write briefly) and gave it to him.  He said he only needed a sentence or two, so I told him just to take his pick.  He replied Never Mind, and said he would get back to me with the results in a day or two.

I got back my original paper with these words added all over and arrows pointing to portions that apparently supported what he claimed were indicators reflecting my personality traits.  These are a reflection of about 90 percent of the words he used.

Stubbron, bull-headed, iron-willed, obstinate, difficult, insistent, demanding, assertive, overriding, inflexible, opinionated, argumentive, mule-headed, and something about acting like a jackass, but I forgot the precise reference made.

Some of these words appeared repeatedly, and some words had arrows connecting them to different parts of where I had written something. meaning it was not one indication but many involved.  I looked at him, and he seemed dead serious.  So you know what I thought?  Must be something to this analysis thing, because he really had it right.  I was all those things and more.  Realizing it may have soften me a bit over time, but I am not sure.

So what is the point of saying this?  Because I often do not start off with the simplest problem or simplest configuration, but decide to see how far the matter can be taken, and that is from the very start.  What I have here is a D-Link router and wiring for up to four PCs to connect with the internet, and that works fine.  So do the PCs that connect to it.  But I was taken by a chance to get a notebook PC at a great price with many features, like a large screen and keyboard, so I went ahead and bought it.  It comes with both wire and wireless internet capabilities, and I just used wire initially.  That was fine.

But my nephew across the road and a bit north of here has little money, and a deal for cable access that he shared with his brother-in-law next door just went to pot, so he got his own access from the cable company.  But he is so busy with helping others that he has little time or interest in using it, and the expense mounts up.  Having a PC is only half the picture, because the internet brings you the world, just like TV does, but in more useful ways.

So I got a Geeks' Wireless-N router with four ports at a bargain price, unplugged my notebook from the D-Link, and just attached the Geeks' router there, and it works fine in that configuration.  I just had a dicken's of a time getting the wireless adapter in my notebook to connect to it, but that has all been solved.  So 4-port D-Link, and port 4 runs to the Geeks' as its WAN, and the notebook is wireless from there.

Some will tell you that this is a bad idea, and others say the Geeks' should just replace the D-Link, but I am sort of stubbron, you know? Oh, of course you do.  So I am not going that way, because it is just the way that everybody else goes.  My nephew's involvement is that I want him to work on wirelessly connecting to my setup so that he can get away from that heavy expense each month, when he gets so little use out of it.  He's a stubbron cuss though, and not inclined to follow my lead on this.  Not sure why.

I got a USB to Wireless adapter at a great price, and he can pick up about six AccessPoints in the neighborhood, but the signals are kind of weak (actually, pretty dang low).  I'm trying to convence him to look at some of the many online postings about making your own directional antenna or reflector, some boosting signals by 12 dB to 24 dB, and that is a tremendous amount of gain, so if you get any signal at all, you should be able to really pull it in with the right antenna.

But my nephew don't believe it because... Hey, I don't know why he doesn't believe things sometimes, but it kind of makes you mad when you know you are giving him the real lowdown, and he won't take your word for it and he won't bother to check it out for himself.  People can be like that, you know?  Just frustrating and inferiorating, but I don't like to give up on things because... well, that's just the way I am.

So what now?  I want the PCs connected by these two routers to act as they are part of one domain or one workgroup.  I already know this might be super hard because of my chosen configuration, and made even harder by the fact that the PCs might be running either Ubuntu or Windows 2000.  From what I've found so far, this is a task that is just past the scope of what Windows 2000 can do, and you have to move on to XP if you want this to happen.  With Windows, nothing seems beyond its inability at times, but I won't be pushed in that direction.  There has to be another way, and I just have to find it.

Ubuntu has a Network button under Places. and under it, you are suppose to connect to a server.  What server?  What does this server have to be set up as, and how?  Don't know yet.  I installed both Samba and smbfs as some reading has suggested, but nothing significant from either yet.  I may actually have to read something about both.  There is a samba configuraton file, and some suggestions for settings in it in a couple of posts, but some of these posts go way back, and the contents of the config file have changed over time.

What is a domain, and what is a workgroup?  With an IP mask, every binary bit set to 1 reflects a part of a license code that is used in the public domain to direct network traffic from one place to another,  It is like a business address, which brings mail and packages in he door and into the mail room.  Every bit that is left a zero is for internal use only, and can designate specific maildrops in the whole of the business itself. A 201 code for internal use might indicate the first maildrop on the second floor.  Another business might use 201 to indicate a certain office on the second floor.  It makes no difference, because it is just an internal reference.

So in an IP address mask, what does 255.255.255.0 represent?  Translating each of the four goups into binary format, each 255 represents a group of 8 bits all set to 1s, and the 0 represents 8 bits all set to 0s.  In other words, this is what a binary representation of 255.255.255.0 looks like: 11111111.11111111.11111111.00000000.  Now this is lined up with an actual IP address, such as 216.239.51.99 when seen in decimal form, but let's convert that to binary as well:  11011000.11101111.00110011.01100111

So let's stack these two numbers together:
11011000.11101111.00110011.01100111 <-- IP Address in binary form
11111111.11111111.11111111.00000000 <-- IP Address Mask in binary form
-----------------------------------
11011000.11101111.00110011 <-- the part of the IP Address for public routing

Now the logic rule that is applied here is the AND rule.  This states that when binary numbers are aligned like this, the only time you get a "1" below the line is when there are two "1"'s aligned, one below the other, above the line.  The leftmost side has a 1 over a 1, so we put a 1 there below the line.  Anywhere else, we would have a 0 instead.

Now I did not show the rightmost eight 0's for a reason, which is that based on the 1's in the mask. the ones shown below the line make up the public address when used together.  The rightmost group, not brought down as zeros, would be the designator for the mailbox, or the device, that is only a concern of the business itself.  This is referred to as a Class C license.

Note that all the bits in either group total up to 32 bits.  If all 32 bits were flagged with 1s in the address mask, that would be a Class D license, the lowest class, because it then deals only with the public address and leaves nothing left for directing internal routing.  Working backwards, from right to left, if the first 16 bits in the mask are set to 1's, that would be a Class B license, and that would leave you with 16 bits in the IP address for internal routing purpose, which is quite a few.  Coming over to the left one more group, if the first 8 bits in the address mask is set to 1's, then that would leave the remaining 24 bits for internal routing purposes, which is a tremendous amount.

It is a good scheme, but the license administrators did not allow for the extensive growth of the world of networking and gave out way too many Class A and Class B licenses at the beginning.  Many large organizations have tried to get multiple Class C and/or Class D licenses for their needs as a result.

The real result is that the world has been running out of IP addresses for quite awhile, and several solutions have presented themselves.  One is that instead of assigning static IP addresses to each machine, the machines have to rely on requesting an available IP address to be loaned to them for awhile, and that would be a dynamic IP address.  It would not be the same numbers in the IP address each time.

A second approach is to determine a method of associating a specific port number for each machine to both idenfity the machine and to send traffic back to it.  An IP address with added port designation would look something like this:  216.239.51.99:12345 <-- the port address is tagged on the back  As it happens, though, some port designations are already reserved and used for specific services, such as port 80 is used by web browsers to browse the Internet, and you can employ only one port designation per address.

We may ultimately have to move on the third method, which is to find a way to add more bits for use in the IP address and possibly in the address mask.  They have already come up with a method for doing this, but does not fit in with what we are doing now.

Notice that there are just four groups in the present IP address structure, so that is referred to as IPv4, and that is what is being used today.  The new form adds two more groups, taking us from 32 bits to 48 bits, and that is called IPv6.  As more and more networking devices are made available that have the option to work with IPv6, we may eventually get to a point where we either switch over, or subdivide the world network where part of it continues to use just IPv4, the rest uses IPv6, and we divise methods to interchange traffic between them  IPv6 offers such a vast array of addresses that there is some confidence that it will never be depleted.  But of course they thought that about IPv4 once too,  It isn't that we can't switch over.  It is just going to be expensive to do and disruptive, and how much it will cost and who will be hurt or damaged by mistakes made is impossible to determine beforehand.

Anyway, that is the good news.  By good, I mean we aren't there yet.  But what I want do do now is get a home network set up behind an interactive pair of routers, one serving as an access point, and be able to interconnect and talk between them and use shared things like printers.  

Keep in mind, like I said earlier, that this is to be a combo of Ubuntu and Windows 2000 working together, if I can find a way to make it happen.
So ideas are welcomed, tips even more so, and maybe some progress will get made.  I'd like to think so.  There seem to be so many settings involved, from Samba to the routers themselves, and it is hard to find information on what all those settings are for and what they ought to be set to.

I paid my dues by telling you some of what I know, but there is much I haven't had a hand at yet.  I guess my first real questions are:

How to get all the PCs involved to see each other?  They actually only see themselves at this point.

What should the local server be, Windows or Ubuntu?  Can I make it so that it can be either?  What needs to be done to make this happen?

And that is for starters.

---

### Post by gordintoronto on 2010-02-12
"Ubuntu has a Network button under Places. and under it, you are suppose to connect to a server."  No, you can connect to a "share" on any computer, Windows or Linux.

A domain is a network with a domain controller.  Most domain controllers use Windows Server, but a computer running Linux can be a domain controller.  If you had a domain controller, you would know it.  Therefore, you have a workgroup.  Or maybe several of them.

Your dialogue on IP addresses was completely irrelevant, and even somewhat incorrect.  Your network has a bunch of computers with addresses which begin 192.168.1(???), and NAT is used for communication to the Interent.

All your machines need to be in the same workgroup.  I have no experience with W2000.  In Windows XP, you can right-click on "my computer" and select Properties; one of the editable Properties is "workgroup."  (W2000 might be the same.)  I am a big believer in using recognizable, unique workgroup names, such as "foxynet".  In Windows Explorer, you can right-click on a folder and select "share".  You also must have "file and printer sharing" enabled in Networking.

The workgroup name goes in a file in Linux, you can open a terminal and enter the command:
sudo gedit /etc/samba/smb.conf

The workgroup is in the global settings, you can change it, save the file and reboot.

Once everybody is in the same workgroup, you can open the network Place, double-click on "windows network," double-click on the workgroup, double-click on a computer which hosts a share, double-click on the share, and there you are.

You would get better answers if you wrote shorter questions.

---

### Post by bab1 on 2010-02-12
> **oldefoxx said:**
> ...

My nephew's involvement is that I want him to work on wirelessly connecting to my setup so that he can get away from that heavy expense each month, when he gets so little use out of it.  He's a stubbron cuss though, and not inclined to follow my lead on this.  Not sure why.

I got a USB to Wireless adapter at a great price, and he can pick up about six AccessPoints in the neighborhood, but the signals are kind of weak (actually, pretty dang low).  I'm trying to convence him to look at some of the many online postings about making your own directional antenna or reflector, some boosting signals by 12 dB to 24 dB, and that is a tremendous amount of gain, so if you get any signal at all, you should be able to really pull it in with the right antenna.
See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://www.google.com/search?hl=en&q=cantenna+wireless+antenna+pringles&aq=f&aqi=&oq=")on how to make an antenna out of a Pringles can.> 
...

Ubuntu has a Network button under Places. and under it, you are suppose to connect to a server.  What server?  What does this server have to be set up as, and how?
This is to connect to any server on you LAN.  It can be Samba or Web (HTTP) or some such.  > 

What is a domain, and what is a workgroup? 
In its most basic terms a domain is any IT entity that has common administration.  A windows domain is as @gordintoronto has described.  An Internet domain is a domain that you control with a name supplied by ICANN.  A workgroup is a domain also.  It is a browsing domain maintained in Windows or Samba.> 

With an IP mask, every binary bit set to 1 reflects a part of a license code that is used in the public domain to direct network traffic from one place to another,  It is like a business address, which brings mail and packages in he door and into the mail room.  Every bit that is left a zero is for internal use only, and can designate specific maildrops in the whole of the business itself. A 201 code for internal use might indicate the first maildrop on the second floor.  Another business might use 201 to indicate a certain office on the second floor.  It makes no difference, because it is just an internal reference.
Not really.  The subnet mask is a filter to separate the network address from the individual hosts on that network  See [**_[COLOR="DarkGreen"]here[/COLOR]_**]("http://www.jodies.de/ipcalc?host=192.168.0.0&mask1=24&mask2=") for a great explanation.> 

So in an IP address mask, what does 255.255.255.0 represent?
The subnet mask filter> 

  Translating each of the four goups into binary format, each 255 represents a group of 8 bits all set to 1s, and the 0 represents 8 bits all set to 0s.  In other words, this is what a binary representation of 255.255.255.0 looks like: 11111111.11111111.11111111.00000000.  Now this is lined up with an actual IP address, such as 216.239.51.99 when seen in decimal form, but let's convert that to binary as well:  11011000.11101111.00110011.01100111

So let's stack these two numbers together:
11011000.11101111.00110011.01100111 <-- IP Address in binary form
11111111.11111111.11111111.00000000 <-- IP Address Mask in binary form
-----------------------------------
11011000.11101111.00110011 <-- the part of the IP Address for public routing [COLOR="Red"]**<---incorrect**[/COLOR]

Now the logic rule that is applied here is the AND rule.  This states that when binary numbers are aligned like this, the only time you get a "1" below the line is when there are two "1"'s aligned, one below the other, above the line.  The leftmost side has a 1 over a 1, so we put a 1 there below the line.  Anywhere else, we would have a 0 instead.

Almost but not quite.  With the mask under the IP address we compare (from left to right.  All of the bits above the mask where the mask is 1 contiguously (i.e 111111111111 no 0's in between) is the network.  As soon as there is a 0 in the subnet mask we have the border to the individual host addresses on that network.> 

Now I did not show the rightmost eight 0's for a reason, which is that based on the 1's in the mask. the ones shown below the line make up the public address when used together.  The rightmost group, not brought down as zeros, would be the designator for the mailbox, or the device, that is only a concern of the business itself.  This is referred to as a Class C license.
In more modern terms this is the 254 host addresses in a 24 bit network (i.e. 128.125.1.0/24).  The term *Class C *is not used much anymore.> 


Note that all the bits in either group total up to 32 bits.  If all 32 bits were flagged with 1s in the address mask, that would be a Class D license, the lowest class, because it then deals only with the public address and leaves nothing left for directing internal routing. 
Come on now -- Class D is multicast and it is 224.0.0.0 to  	239.255.255.255.  255.255.255.255 is the broadcast address for all on the network.> 
 Working backwards, from right to left, if the first 16 bits in the mask are set to 1's, that would be a Class B license, and that would leave you with 16 bits in the IP address for internal routing purpose, which is quite a few.  Coming over to the left one more group, if the first 8 bits in the address mask is set to 1's, then that would leave the remaining 24 bits for internal routing purposes, which is a tremendous amount.

It is a good scheme, but the license administrators did not allow for the extensive growth of the world of networking and gave out way too many Class A and Class B licenses at the beginning.  Many large organizations have tried to get multiple Class C and/or Class D licenses for their needs as a result.

The real result is that the world has been running out of IP addresses for quite awhile, and several solutions have presented themselves.  One is that instead of assigning static IP addresses to each machine, the machines have to rely on requesting an available IP address to be loaned to them for awhile, and that would be a dynamic IP address.  It would not be the same numbers in the IP address each time.

There is no loaning of IP addresses.  You can only get an address that the DHCP administrator adds to the dhcp pool.  These come from your network.  These are *leased *as in it is yours as long as the host interface is up.> 

A second approach is to determine a method of associating a specific port number for each machine to both idenfity the machine and to send traffic back to it.  An IP address with added port designation would look something like this:  216.239.51.99:12345 <-- the port address is tagged on the back  As it happens, though, some port designations are already reserved and used for specific services, such as port 80 is used by web browsers to browse the Internet, and you can employ only one port designation per address.
This is not a second approach, but rather a part of the TCP/IP protocols.  All WAN TCP/UDP communication requires a TCP/UDP port.  The first 1024 ports are controlled.  The rest of the 65536 ports are available for applications to use unless they are blocked. >  

We may ultimately have to move on the third method, which is to find a way to add more bits for use in the IP address and possibly in the address mask.  They have already come up with a method for doing this, but does not fit in with what we are doing now.
IPv6> 

Notice that there are just four groups in the present IP address structure, so that is referred to as IPv4, and that is what is being used today.  The new form adds two more groups, taking us from 32 bits to 48 bits, and that is called IPv6.  
Addresses in IPv6 are 128 bits long> 

As more and more networking devices are made available that have the option to work with IPv6, we may eventually get to a point where we either switch over, or subdivide the world network where part of it continues to use just IPv4, the rest uses IPv6, and we divise methods to interchange traffic between them  IPv6 offers such a vast array of addresses that there is some confidence that it will never be depleted.  But of course they thought that about IPv4 once too,  It isn't that we can't switch over.  It is just going to be expensive to do and disruptive, and how much it will cost and who will be hurt or damaged by mistakes made is impossible to determine beforehand.
IPv6 is running now.  There are tunnel brokers to allow for interoperability between IPv4 and IPv6 networks.> 

Anyway, that is the good news.  By good, I mean we aren't there yet.  But what I want do do now is get a home network set up behind an interactive pair of routers, one serving as an access point, and be able to interconnect and talk between them and use shared things like printers.  
... I guess my first real questions are:

How to get all the PCs involved to see each other?  They actually only see themselves at this point.  
What does "see each other" mean to you?  Does it mean browsing folders and files like Windows or FTP services or just pinging each other? > 

What should the local server be, Windows or Ubuntu?  Can I make it so that it can be either?  What needs to be done to make this happen?
If you have A Windows host you would need Samba on the Linux hosts.  Windows sharing uses the SMB/CIFS protocol.

---

### Post by oldefoxx on 2010-02-15
This discussion has really been informative, at least for me.  I studied networking issues years ago under the guidance and with the material that several key consulting firms provided to my company at a fee.  It seems that quite a bit has changed during the intervening time, which is a span of something like 15 years.  Now either the information at the time was incorrect, or your information is slightly off, or there has been some advancement in that time so some change has emerged, which is entirely possible.

So thanks for taking the time and making the effort to set things right.  You know, one thing of particular interest in what you say is not only that IPv6 more extensive than I was aware of, but that you say that in the subnet mask, as you check from left to right, you say that the first 0 is the key to where the mask splits.  Back then, we were taught that each 1 and each 0 performed in the matter I explained, and that was regardless of the order involved.
So you could have a mask like this, 255.255.255.0, which is more or less common, or you might come up with a scheme that looked more like this: 173.232.115.67.  That means that the public address bits could be scattered among the remaining bits.

Why you would ever want to do this was unknown, and it would not work properly with any other submask scheme.  So what was adopted was the 1s to the left and the 0s to the right, which still holds true today.  You know, the really odd thing about this is that they could have just designated by count where the first zero was to occur, and instead of having to enter 255.255.255.0, you could have just stated 25.  Even with all the bits coming with IPv6, one 8-bit value that can count positively from 0 to 255, would be more than sufficient to indicate where that first 0 would lie in the mask.

Your reference to 192.168.1.(?) is only partially correct.  True, behind the routers we buy, the 192.168 are apparently fixed, but some vendors use 192.168.0 (D-Link being one) and others use 192.168.1 (Linksys as an example)  The distinction is that the router itself recognizes either the 192.168.0 or the 192.168.1 as reflecting some device that must be connected on its backside, to which that router would have had to assigned address that begins with the same first three groups.  This is how my wireless is able to work with the D-Link, because the Wireless uses 192.168.1 as belonging to it, so when I use 192.168.0 instead, it just hands it off to the D-Link, which recognizes it as belonging in its addressing range.  The fourth and last group for both is usually fixed at being in the range of 100 to 250.
Had both routers the same addressing scheme. they could not work through each other in the manner in which I have them attached.

So what address was assigned to your PC?  I haven't ventured with Linux enough to know the answer to this, but with Windows, you can go to the command line and enter IPCONFIG and find out.  Use IPCONFIG /A instead, and you will find out a whole bunch of other information as well.  And you can use PING <address or URL> to see if you can reach any other device or site anywhere, and how long it takes to get there, what with network delays.  Use IPCONFIG /H or IPCONFIG /? and find out what else IPConfig can do for you, like reset your network adapter if you are having trouble connecting.

I admit my knowledge is showing that it is rather dated, but that is the price you pay when involved in a fast changing world, and especially a fast changing industry.

One more thing that bugs me about Windows, specifically Win 2k in this case, is that the Network Wizard rejects any request to add any device address that begins with 192.168.0 or 192.168.1 because it sees them as being invalid.  Not that they are, but back when Win 2k was out in force, there were no routers to address or assign addresses.  Now I guess I will have to find a way around if I want my PCs on the back end to communicate with each other.  So far I can see I can't call on the wizard, and do not yet know where those addresses end up at.

---

### Post by bab1 on 2010-02-15
> **oldefoxx said:**
> ... but that you say that in the subnet mask, as you check from left to right, you say that the first 0 is the key to where the mask splits.  Back then, we were taught that each 1 and each 0 performed in the matter I explained, and that was regardless of the order involved.
So you could have a mask like this, 255.255.255.0, which is more or less common, or you might come up with a scheme that looked more like this: 173.232.115.67.  That means that the public address bits could be scattered among the remaining bits.

Why you would ever want to do this was unknown, and it would not work properly with any other submask scheme.  So what was adopted was the 1s to the left and the 0s to the right, which still holds true today.  You know, the really odd thing about this is that they could have just designated by count where the first zero was to occur, and instead of having to enter 255.255.255.0, you could have just stated 25.  Even with all the bits coming with IPv6, one 8-bit value that can count positively from 0 to 255, would be more than sufficient to indicate where that first 0 would lie in the mask.

[COLOR="darkBlue"][B]It works as follows:  The address 173.232.115.67 does not in itself describe the nature of the network it resides in.  To know the network that it belongs in you need to know the boundaries of the network.  As a network engineer or network administrator you need to know the network address, the broadcast address and the amount of host in the network.

Since you have used the subnet mask of 255.255.255.0, we will start there.  What does it represent bit wise.  I see it as 11111111.11111111.11111111.00000000 (I have added the periods to separate the octets).  This can also be expressed as a 24bit subnet mask.  How many bits are expressed as 1&#8217;s?  I see 24.  This can also be notated as /24.  In conjunction with an IP address it can define the network and host sections of an IP address.

In the above example the IP address of 173.232.115.67 with a 24 bit (/24) is in the 172.232.115.0/24 network.  Let&#8217;s lay it out visually:

```

172.232.115.67 = [COLOR="DarkSlateGray"]10101100.11101000.01110011.[/COLOR][COLOR="Green"]01000011[/COLOR] [COLOR="Red"]<-IP address[/COLOR]

255.255.255.0  = 11111111.11111111.11111111.00000000 [COLOR="Red"]<-Subnet Mask[/COLOR] 
And&#8217;d numbers  = 11111111.11111111.11111111.00000000
===================================================
Network ID     = [COLOR="DarkSlateGray"]10101100.11101000.01110011[/COLOR]	     [COLOR="Red"]<-network address[/COLOR]
Host ID  		                   [COLOR="Green"].01000011[/COLOR] [COLOR="Red"]<-Host address[/COLOR]
```

The anding works as follows: If you have a 1 bit in the subnet mask then the bit from the address is used to express the network ID.  If you have a 0 (zero) in the subnet mask then the bit from the address is NOT used to express the network ID.

Looking at the above address it is obvious that the boundary between the network portion of the IP address and the host address is where the flipped bits (1) stop and the un-flipped bits (0) start in the subnet mask.

Let&#8217;s say that the subnet mask is 255.255.0.0 (16 bits (/16).  This would be expressed visually this way:
 
```

172.232.115.67 = [COLOR="DarkSlateGray"]10101100.11101000.[/COLOR][COLOR="Green"]01110011.01000011[/COLOR] [COLOR="Red"]<-IP address[/COLOR]

255.255.0.0    = 11111111.11111111.00000000.00000000 [COLOR="Red"]<-Subnet Mask[/COLOR] 
And&#8217;d numbers  = 11111111.11111111.11111111.00000000
===================================================
Network ID     = [COLOR="DarkSlateGray"]10101100.11101000.[/COLOR]	     [COLOR="Red"]      <-network address[/COLOR]
Host ID                            [COLOR="Green"]01110011.01000011[/COLOR] [COLOR="Red"]<-Host address[/COLOR]
```
The network in this case is 172.232.0.0 The host address looks funny but it is correct.  It is 115.67 in dotted decimal (to represent the bits) or the 14720th out of 65533 host addresses.                 
[/B][/COLOR]
> 

Your reference to 192.168.1.(?) is only partially correct.  
I'm not sure what you've been smokin', but I never mentioned 192.168.1.0 networks at all.> 
True, behind the routers we buy, the 192.168 are apparently fixed, but some vendors use 192.168.0 (D-Link being one) and others use 192.168.1 (Linksys as an example)  The distinction is that the router itself recognizes either the 192.168.0 or the 192.168.1 as reflecting some device that must be connected on its backside, to which that router would have had to assigned address that begins with the same first three groups.  All the D-link's and Linksys SOHO and home routers I've seen are configurable  They are set to a default though.> This is how my wireless is able to work with the D-Link, because the Wireless uses 192.168.1 as belonging to it, so when I use 192.168.0 instead, it just hands it off to the D-Link, which recognizes it as belonging in its addressing range.  These devices can be configured in multiple ways to do many things.  It doesn't change the protocol.> The fourth and last group for both is usually fixed at being in the range of 100 to 250.Once again, the number of host ID addresses is 254 valid numbers.  The network number is 0 and the broadcast address is 255.  These routers have the default DHCP pool set to 100 numbers usually. As you say, they are typically set to somewhere in the middle of the range.> 
Had both routers the same addressing scheme. they could not work through each other in the manner in which I have them attached.
There is an RFC that describes the *private *non-routable networks. See [**_here_**]("http://en.wikipedia.org/wiki/Private_network").  Any of these *private networks *should work on and but the most basic routers/residential gateways.  That your D-Link wont allow you to configure 192.168.[COLOR="Red"]24[/COLOR].0/24 as your private network does not mean that it is not valid in regards to the protocol. > 

So what address was assigned to your PC?  
I have 7 devices on my home network.  I use 192.168.1.1, 192.168.1.12, 192.168.1.14, 192.168.1.150, 192.168.1.52 and 192.168.200.  I have used 10.0.0.0/16 (a subnet of 10.0.0.0/8 for other projects and clients.  I could have just as easily used a 192.168.0.0/16 network but clients think a 10.0.0.0/16 network is for larger installs and I have stopped trying to explain.

---

### Post by oldefoxx on 2010-02-15
I thank you for your patience with an old, retired systems engineer, who was not up to all that was expected of a network engineer, which were of the newer breed and given given better and more directed training.  Very informative, and worth hearing from someone in the know.  So why bother showing what I know or don't know in this matter?  Because how else are you likely to learn something new?  And while I gain something, I would hope that others gained more.  Passing on knowledge is an important part of what we all have to contribute, and I do what I can in that regard, even if it is only to inspire a discussion that goes beyond the scope of what I really know and understand.  So thanks again.

I've got other pressing matters to attend to for a bit, some of which involve other threads, but I fully mean to return to this one and push forward with some of the issues already stated.  Learning is just part of doing, and there is more of both to contend with on this subject.

---

