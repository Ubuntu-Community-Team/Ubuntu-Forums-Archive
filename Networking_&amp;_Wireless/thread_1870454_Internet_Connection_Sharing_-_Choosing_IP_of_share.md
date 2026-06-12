---
title: "Internet Connection Sharing - Choosing IP of shared computer"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by aloogobi on 2011-10-27
Hi, I'm using Ubuntu 10.04. I recently purchased a surround sound system that does not have wireless in built. Since my router is upstairs, and my surround sound downstairs, I thought I would use an old laptop running ubuntu provide internet to the surround sound system using internet connection sharing. 

The setup is thus:

Router (192.168.1.1) ---> Ubuntu Laptop's Wireless --> Surround Sound receiver via Ubuntu Laptop's ethernet


I have internet connection sharing working fine. The only issue is that the IPs assigned by the Ubuntu Laptop to the shared receiver are in the format of 10.x.x.x. I was hoping to get IPs similar to the rest of the network, ie 192.168.1.x. How can I achieve this? I think I need to have the surround sound system setup with such an IP in order to see my ubuntu server running mediatomb. I replaced the surround sound with my macbook to test the network. It appears I can't find things like my Playstation when I am behind the Ubuntu laptop sharing the internet. However, when I'm using my macbook on the network as usual, I can discover the playstation without issue. This makes me believe that from behind the Ubuntu Laptop sharing the internet, I can't see things on my local network (though I can ping hosts my IP eg: 192.168.1.107, but not by hostname eg: UbuntuServer.local). 

I'm by no means an networking guru, so if I can make the setup work with the current IPs, then let me know as that would work too. Ultimately, I would like for the surround sound receiver to recognize the media tomb ubuntu server. 

Thanks in advance.

---

### Post by aloogobi on 2011-10-28
Any suggestions would be appreciated - even if you're just brainstorming - if it's something I can try and work with, it may help.

Thanks

---

### Post by jonobr on 2011-10-28
AFAIK the way internet connection sharing works is that your machine doing the sharing has two interface, one to the internet side and the other to the internal network.

So its assuming your going from an internet connection and sharing that internet connection to internal addresses.
hence the internet connection sharing name.

In that case your routing from one public side to an internal private side.

You have a public connection, going into a private network and it appears your going to another private network.

In both cases you will need to nat and route between both interfaces.

I believe This is why windows assigns an ip address scheme of 192.168.137.x. on the home network side as it will not conflict with the default 192.168.1.x
In your case its assigning addresses in the 10 as your wlan0 is already on a 192.168.1 address

So now , if you wanted to have the same address space on your home network side, you are no longer routing between the interface, you should be bridging which is something a bit different.

If you did manage to change the home network to a 192.168.1 address space  (which I think is done in /etc/dnsmasq.conf) AFAIK it would not work as the addresses are the same and it would not know to route to the other interface

Again to use the same address space on both sides you would need to bridge between the two interfaces.

My question is whats wrong with the 10.x ?
This is valid private ip address space much like 192.168.1.x 
and again in windows you would be getting a 192.168.137.x which you can change but requires you going into the registry and a bit of voodoo

see [Here for a description on private address spacing.]("http://en.wikipedia.org/wiki/Private_network")

---

### Post by aloogobi on 2011-10-28
Jonobr, 

Thank you very much for that detailed response. When I get a 10.x address on the shared device (ie the surround sound receiver) I can access the internet without any issues. My problem lies in the fact that my surround sound receiver cannot see my ubuntu server running mediatomb, address 192.168.1.107. As an experiment (mentioned in my initial post), i replaced the surround sound with my macbook to see if it would detect my PS3 (address 192.168.1.108  ) and it could not. However, if I'm using my macbook on my wireless network as normal, it finds it without any issue. So I assumed that the surround sound system can't detect the other servers on my 192.168.1.x network when using an ip of 10.x. I will say however, that when I have my macbook setup behind the share computer, that I can ping the hosts, but only if I use the ip address, and not the host name (eg: using 192.168.1.107 instead of ubuntu.local). Do you know why that is?

Also, do you know if there is a way to setup ubuntu to act as a bridge and not a router. Essentially, this is what I am after, but it feels like I may have to buy another router to achieve this. 

Thanks again.

---

### Post by aloogobi on 2011-10-28
Found this on bridging: 
[http://www.ezunix.org/index.php/Set_up_bridge_interface_in_Ubuntu_Linux](http://www.ezunix.org/index.php/Set_up_bridge_interface_in_Ubuntu_Linux) 

I'll give it a shot tonight and see if it works

---

### Post by jonobr on 2011-10-28
Yep you found the link on setting up as a bridge.

Im going to read read your post and think about it in the next few hours as I am a bit confused on the actual issue.

Let me get back to you later

---

### Post by jonobr on 2011-10-31
any luck with your bridging?

---

### Post by aloogobi on 2011-11-02
> **jonobr said:**
> any luck with your bridging?

Negative. It seemed so straight forward, but after bridging the two, the computer before the mediaserver would not connect to my wireless anymore. I read somewhere that newer versions of Ubuntu won't support bridging. 

This link suggests using NAT instead. Haven't given it a go or read anything about it yet. 

[http://serverfault.com/questions/152363/bridging-wlan0-to-eth0](http://serverfault.com/questions/152363/bridging-wlan0-to-eth0)

---

### Post by malcmail on 2011-11-04
I'm having a more fundamental issue with this but the way I got it working was to add the route to the 10.x.x.x machine in my router. Going out from the 10.x.x.x machine was never a problem though.

---

