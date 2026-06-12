---
title: "Resolv.conf overwritten by Network Manager wipes my settings"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by mac1984user on 2010-01-13
Hello,
 
I have connected my girlfriend's laptop to a university network (in halls/dorms) and have had to make some manual changes to /etc/network/interfaces (for static IP purposes) and /etc/resolv.conf (to enter DNS server info). Everything was working great with these settings, but after leaving her room, accessing wireless in the library, and then returning to her hardwired connection, her internet no longer works.
 
When I went back to the resolv.conf file, I found that all of my changes were deleted and replaced with something to the effect of 'Settings managed by Network Manager'. It appears that Network Manager is overwriting the settings I made in resolv.conf. Re-entering this information solves the problem, but I would not expect my girlfriend to have to do this every time she wants to access the internet.
 
The computer must be on a static IP when connected via cable, as it needs to connect to the university's DNS servers. I don't believe uninstalling Network Manager is the way forward, because I worry that my g/f won't be able to easily switch between wireless and hardwired as the need arises.
 
Does anyone know how to resolve this issue? How can I keep my resolv.conf file from being overwritten regularly by Network Manager? I read somewhere that entering 'ifdown eth0' in Terminal, making the changes to the resolv.conf file and then going back into Terminal and entering 'ifup eth0', the problem can be solved. Has anyone else had any luck with this. Any help would be greatly appreciated.

---

### Post by x33a on 2010-01-13
To prevent resolv.conf from being overwritten, do
```
sudo chattr +i /etc/resolv.conf
```

---

### Post by mac1984user on 2010-01-13
Thanks, I'll try that. Would you mind providing me with the code to reverse that command if, for some reason in the future, I ever want the resolv.conf to be overwritten?
 
I look forward to any other solutions others might have and appreciate the assistance. We had so many problems getting my girlfriend's new laptop up and running. We've had a lot of issues with Windows 7 incompatibilities with her model of Toshiba laptop. A reinstall of Vista did not work, and I do not want to have to resort to XP. She's extremely happy with Ubuntu (which makes me happy), and I would hate to have to move back to XP (especially on a laptop that's less than four months old) just so she can have a stable internet connection experience.
 
Cheers!

---

### Post by x33a on 2010-01-13
for reverting that
```
sudo chattr -i /etc/resolv.conf
```

---

### Post by suseendran.rengabashyam on 2010-01-13
Hi,

You can mention your DNS servers in /etc/network/interfaces file as shown below. You will need to install resolvconf package for these DNS settings to work. In this approach, you do not need to add any DNS server entries to /etc/resolv.conf file manually.

1) # sudo apt-get install resolvconf

2) Add the following 2 lines in /etc/network/interfaces file under your configuration for your interface(eth0?):

dns-nameservers x.x.x.x y.y.y.y
dns-search xyz.com

Reboot your machine and see if these DNS servers are added automatically to your /etc/resolv.conf file.

Since your wireless interface will continue to be managed by the NetworkManager, there should not be any problem when you are using Wireless instead of the wired connectivity.

Let me know if this helps.

---

### Post by mac1984user on 2010-01-13
Hello,

Unfortunately, none of the solutions offered above worked properly. Suseendran, resolvconf installed fine, but the changes to the interfaces file were not automatically ported over to the resolv.conf file after boot-up, so I was faced with the same problem. I decided to uninstall resolvconf as it was more difficult to change settings than it was to simply make a few changes in the resolv.conf file (at least I can GET internet somehow). It's just inconvenient whenever I detach wired ethernet, go to a wireless hotspot and come back to find that all the resolv.conf files were deleted by network manager.

x33a, your solution was quite good in the sense that it certainly kept network manager from overwriting the resolv.conf file. Every time I wanted to use the wired ethernet, it connected without fail. However, when I went to a wireless hotspot, wireless could not connect because Network Manager could not alter the resolv.conf file to include the IP address produced by the wireless connection. So I was stuck in a SECOND quandry. It's really frustrating, but I appreciate the suggestions.

So, basically, I'm back to square one. I tried to just enter in the same DNS server names and the fixed IP address directly into Network Manager, but that didn't work either. If my girlfriend never leaves the desk in her room, her wired ethernet works fine. If, however, she needs to go to the library or to class with her laptop and connects to the wireless internet, upon returning to her room, she now has to manually edit the resolv.conf file every time she wants to access the internet. She's probably less bothered about it than I am, but it seems a bit ridiculous that she can't simply choose to use wireless one minute and wired the next without so much hassle. I'm really pissed off with Toshiba for selling a laptop with a crap BIOS that doesn't accept Windows 7 installations. We literally bought it AFTER Windows 7 was released. If you go on the website, the Satellite Pro L300D is STILL shipped with Windows Vista 32-Bit, but now they advertise it as having an updated BIOS. Go figure! Ridiculous. We both love Ubuntu so much, but I just don't know how to get around this one issue. Any further advice would be greatly appreciated.

---

### Post by Iowan on 2010-01-13
If the connection were via DHCP, I'd suggest using the "prepend" option in */etc/dhcp3/dhclient.conf*.

---

### Post by mac1984user on 2010-01-14
If only it were a connection through DHCP... my life would be so much easier.

---

### Post by Iowan on 2010-01-14
Some background information... what static address setting is it that won't work via Network Manager's manual setting?

---

### Post by mac1984user on 2010-01-15
Hello,
 
I'm not certain why it's not working in Network Manager; I think it's because I need more information than Network Manager has fields for. This computer network needs a specific computer name, a network address, subnet mask, gateway, fixed IP, and three specific DNS servers. So, the only way to include all this information is to go into both the /etc/network/interfaces file to include the search domain, the static IP address, gateway, network, subnet, etc. Then I have to go into the /etc/resolv.conf to add the DNS servers.
 
When I enter the DNS servers into Network Manager, it doesn't add them to the resolv.conf file and I cannot access the internet. So trying to get these settings to work within the GUI just doesn't seem possible. Should I delete network manager? In so doing, would I lose the ability to access wireless signal and connect to wired ethernet? Is there an alternative to Network Manager that offers more settings? When I can get back to that computer, I'll post the details of what's required by the school network.
 
Cheers

---

### Post by mac1984user on 2010-01-15
Okay, these are the settings I end up plugging into the /etc/resolv.conf file and the /etc/network/interfaces file in order to get static IP to work within the schools network, which has its own designated DNS addresses (I've removed the final numerals in each address) and replaced the universities access address with [www.----.com]("http://www.----.com").

As I said before, I need to be able to keep the settings within the resolv.conf file in order for the wired internet to work properly. These settings work fine until we access wireless somewhere else and then come back to the wired connection. We then have to re-enter the same code into the resolv.etc every time before connecting to the network. Even while the computer is connected, Network Manager does not recognise the connection, though the internet *does* work.

/etc/resolve.conf
```
search www.----.com
nameserver 131.111.xxx.x
nameserver 131.111.x.xx
nameserver 131.111.xx.xx
```/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
address 131.111.xxx.xxx
netmask 255.255.xxx.x
network 131.111.xxx.x
broadcast 131.111.xxx.xxx
gateway 131.111.xxx.xx
```Is there a way to enter some instructions for wireless in the interfaces file? Then I can write-protect the file, as suggested above, so the settings aren't reset by Network Manager.

Thanks.

---

### Post by changingstate on 2010-01-15
[http://ubuntuforums.org/showthread.php?t=315655](http://ubuntuforums.org/showthread.php?t=315655)

---

### Post by suseendran.rengabashyam on 2010-01-18
Hi,

The entries which you have made in /etc/resolv.conf and /etc/network/interfaces can also be made using the Network Manager applet.

Go to System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings, change the method from "Automatic (DHCP)" to "Manual". In the "Address" column click on "Add" and enter your IP Address, Netmask and Gateway.

If you want to use Multiple DNS servers, in the "DNS servers:" box, enter the IP addresses of the DNS servers as a comma-separated list.

It should look like this: 131.111.xxx.x, 131.111.x.xx

In the "Search domains:" box enter your university's domain name (without www)

More Details can found in the following link
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
                   [URL="http://10.10.43.151:3000/issues/show/68#"]
[/URL]

---

### Post by beradero on 2010-06-02
try this.. 

cd /etc/NetworkManager/system-connections
sudo vi Auto\ eth0
# below [ipv4]
dns=x.x.x.x;x.x.x.y;...;

---

### Post by jarome on 2010-07-08
I have this problem also on 10.04 with my HP MiniNote 2133.
If I plug in my ethernet, resolv.conf is correct. However, doing any network access (like ping) gives a permission denied!
Connecting my wireless results in a blank resolv.conf file. If I add the nameservers manually, wireless works.
And my /etc/network/interfaces file only has the l0 loopback interface in it.
This all worked in the previous Ubuntu release.

---

### Post by a_flj_ on 2011-01-22
I am by no means an expert, and I use the kde interface instead of the gnome interface, so please take what I'm writing with several grains of salt.

Network manager expects to manage everything related to network connections, including resolv.conf, wired and wireless interfaces and so on, so making such stuff readonly for it should definitely break it.

Network manager allows you to configure various network connections via its own graphical user interface. You can configure each connection whether it should use DHCP, if it should use a fixed IP, what DNS servers it should use, which interface it should go over and whatnot. This information is written into its configuration, somewhere in a subdirectory in a hidden directory in the user's home (I think somewhere beneath .kde or the like on my KDE-based system). Whenever you tell it to connect via a particular connection, it retrieves this information from there, and sets up resolv.conf, interfaces and whatever else is needed corresponding to what you have configured, so there's no need to manually edit DNS servers, resolv.conf or anything else - the network manager will do it for you.

If you bypass the network manager's configuration, of course it won't know how it should configure the machine for various connections. If you don't want to use the network manager's configuration, you may uninstall it and write your own scripts for each connection type. You cannot, however, bypass network manager's configuration and expect it to find out all by its own how to configure networking under various circumstances.

Hope this helps.

br,

flj

---

### Post by jarome on 2011-01-22
It was a bug in Network Manager. It has been fixed for a year now.

---

### Post by Terentius on 2011-10-16
I had this issue in Ubuntu 11.10 and the following did the trick for me, thanks. ```
sudo chattr +i /etc/resolv.conf
```

---

### Post by papaapa on 2011-10-18
> **Terentius said:**
> I had this issue in Ubuntu 11.10 and the following did the trick for me, thanks. ```
sudo chattr +i /etc/resolv.conf
```

This does not work on 11.10. I try it. If we had write as dns 8.8.8.8 network manager write this to /etc/resolv.conf. If we lock the /etc/resolv.conf, this is not problem for network manager. Network manager still use 8.8.8.8. You can edit, remove, lock the /etc/resolv.conf file, this will not change anything. I try it many many times.

I need to change my DNS from terminal. I open a thread here: [http://ubuntuforums.org/showthread.php?t=1863755](http://ubuntuforums.org/showthread.php?t=1863755) But could not help me anyone yet...

---

### Post by jramey on 2013-04-26
sudo resolvconf --disable-updates

---

### Post by oldos2er on 2013-04-26
Closed, please don't bump old threads.

---

