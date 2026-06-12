---
title: "Virtualbox &amp; Wireless Networking + USB Support"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by mustanglover32 on 2010-02-17
Virtualbox, is great, except that I have no wireless networking or USB support.

Problem one, is USB support.  As far as I know there is a personal free use version of Virtualbox that includes USB support, however I can't find this copy to download it.  Any ideas where I can find it?

Second problem, I have an integrated wireless networking card in my laptop, that Ubuntu recognizes with no problems, but Virtualbox can't even "see" the device.  I found a tutorial that addresses this know issues with wireless and Virtualbox, but I don't understand the instructions

Source: [https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)
Excerpt:

> **Wireless Networking**

 Setting up a normal bridged network generally doesn't work if you're bridging from a wireless card to [VirtualBox]("https://help.ubuntu.com/community/VirtualBox"). A simple script that utilises the parprouted tool will allow your VM full access to the wireless network. 
You will require parprouted to do this: 

sudo apt-get install parproutedNext, using your favorite text editor, create and edit the script, for example: 

sudo nano /etc/network/if-up.d/vbox_networkThen, enter the script (replacing $USER with your username (or whoever you intend to run virtualbox as)). Replace wlan0 with the name of your wireless interface. Use an available IP address on your network for tap0 (I have used 192.168.1.100 in this case): 

sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u $USER
ip link set tap0 up
ip addr add 192.168.1.100/24 dev tap0
parprouted wlan0 tap0Finally, make sure the new file is executable by root: 

sudo chmod 700 /etc/network/if-up.d/vbox_networkNow your networking script is installed, the virtual interface tap0 will be available on boot for [VirtualBox]("https://help.ubuntu.com/community/VirtualBox"). Rather than reboot, let's just run the script now: 

sudo /etc/network/if-up.d/vbox_networkThe final thing to do is tell [VirtualBox]("https://help.ubuntu.com/community/VirtualBox") to use the new virtual device tap0. Open [VirtualBox]("https://help.ubuntu.com/community/VirtualBox"), highlight a VM and click settings. Now choose the network option and select Host Interface on the 'attached to' drop down menu. In the Interface Name text box, enter: tap0 
Click ok and start your VM. The VM should now behave as though it was another physical machine on your network!! 
For more information on the process up to this point, please visit [Bridged Networking with VirtualBox on Linux Hosts]("http://home.nyc.rr.com/computertaijutsu/vboxbridge.html") 
 
**Using DHCP in the Guest VM**

 It was possible to get DHCP to work on the guest virtual machine. Instructions were taken from [here]("http://www.savvyadmin.com/virtualbox-wireless-bridging-with-dhcp/"). Because parprouted does not relay multicast, we need to use an additional helper daemon to manage this. I tried dhcp-helper and bcrelay, and had the most success with bcrelay. 
Use it as follows: 

sudo apt-get install bcrelay
sudo bcrelay -i tap0 -o wlan0At this point, my /etc/network/if-up.d/vbox_network is as follows: 

 #!/bin/sh
sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u jacob
ip link set tap0 up
ip addr add 192.168.1.200/32 dev tap0
parprouted tap0 wlan0  &
route add -net 192.168.1.0 netmask 255.255.255.0 tap0
bcrelay -i tap0 -o wlan0 &It seems that I have to start the script by hand after boot. Other than that, host networking now seems to work fine (this issue should be solved by adding the "#!/bin/sh" line just at the beginning of the script. 

Any ideas?

---

### Post by mustanglover32 on 2010-02-20
bump

---

### Post by mustanglover32 on 2010-02-21
bump

---

### Post by bpalone on 2010-02-21
I didn't catch which version of Ubuntu you are using, but if you are using a newer release then USB will work out of the box with the PUEL version you can get from: [http://www.virtualbox.org/]("http://www.virtualbox.org/")

Download the manual while you are there, it has lots of good info in it.

As for the wireless, I would see if maybe that gets cured with the change to the PUEL version.

---

### Post by mustanglover32 on 2010-02-22
> **bpalone said:**
> I didn't catch which version of Ubuntu you are using, but if you are using a newer release then USB will work out of the box with the PUEL version you can get from: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Download the manual while you are there, it has lots of good info in it.

As for the wireless, I would see if maybe that gets cured with the change to the PUEL version.


Version is 9.10.  Virtualbox was installed from the Software center and provides no USB support.  Ubuntu supports my USB fine, its Virtualbox that I am having problems with.

Is the version in the Software center not PUEL?

---

### Post by bpalone on 2010-02-22
Go to the link I provided in my first post.  Download the PUEL version of VirtualBox and get the manual while you are there.

Then remove the OPEN Source one you have installed.  Then install the PUEL version you just downloaded.  With the version of Ubuntu you are using, VirtualBox should recognize your USB without any tweaks. (Earlier versions required some tweaks.)  The PUEL version of VirtualBox could possibly cure your other issue too.

PUEL is the Personal Use Evaluation License version you download directly from Sun at the link I provided.

---

### Post by mustanglover32 on 2010-02-22
> **bpalone said:**
> Go to the link I provided in my first post.  Download the PUEL version of VirtualBox and get the manual while you are there.

Then remove the OPEN Source one you have installed.  Then install the PUEL version you just downloaded.  With the version of Ubuntu you are using, VirtualBox should recognize your USB without any tweaks. (Earlier versions required some tweaks.)  The PUEL version of VirtualBox could possibly cure your other issue too.

PUEL is the Personal Use Evaluation License version you download directly from Sun at the link I provided.


Perfect thanks, I didn't realize there was a difference.  Why isn't the PUEL version avaliable in the software center?

---

### Post by bpalone on 2010-02-22
Because it is not OPEN Source.  There may be some legal issues as well, but that is the main reason.

Those distributing and providing repositories, have to be careful what they make available.  Some items are OK in Mexico, but not in Argentina, or America or Europe.  Not all FOSS is totally open.  I am sure someone far more knowledgable than me could explain it better.

That is why you have get your own codecs, because in some countries it is legal to download and use them.  In others it is illegal without compensation to the copyright/patent holders.

However, Sun's PUEL is quite liberal.  So, use it and enjoy.

---

