---
title: "Scrcpy step-by-step"
date: 2024-09-16
forum: Multimedia Software
---

### Post by gipsyshadow on 2024-09-16
I'd like to run Scrcpy with my phone (android 14) and I'd want to ask your help... help for a noob like me indeed :) My goal is to run Scrcpy remotely, I mean via my phone data connection, neither via usb nor via wi-fi.
My first attempt to run Scrcpy via usb in my Ubuntu 22.04 didn't go very well because I just could do everything on my phone and see that in ubuntu but not the vice versa, I mean I couldn't remote control my phone by my PC, I think because I installed an unofficial Scrcpy release (1.25) by a certain "sisco311" from snap store.

So my first question is: how can I install the latest Scrcpy release available for ubuntu?

---

### Post by TheFu on 2024-09-16
sisco311 is the guy who created Scrcpy, so that is the latest.
I tried to get it working a few years ago, after the snap package change, and was unable to get it working.  snap packages have seldom worked for me, but I figured that was just my issue.  I only have 22.04 inside a virtual machine and I'd like to transfer files (or play games) using my computer as the input/video device, not the phone.  Guess I want exactly the opposite of what you seek.

I know Scrcpy worked pre-snap. I used it to play some really busy games on my monitor and to transfer files to/from the phone.  Alas, I got a new phone and the only way I've been able to transfer files was using Ghost Commander via sftp or Nextcloud or by pulling the microSD and connecting that with a USB adapter to my computer. 

What is it that you want to control on the computer from the phone?  There are ssh clients which should allow most things to be controlled, assuming no GUI is necessary. If you need a GUI for transferring files, use Ghost Commander with sftp.  It has a 2-panel (source/destination) layout so transferring files in either direction is possible.

---

### Post by gipsyshadow on 2024-09-17
I decided to try Scrcpy to try to control my phone by my pc remotely via its data internet connection because I read [this page]("https://github.com/Genymobile/scrcpy/blob/master/doc/tunnels.md") about "Tunnels" and "SSH tunnel":
> 
Scrcpy is designed to mirror local Android devices. Tunnels allow to connect to a remote device (e.g. over the Internet).
To connect to a remote device, it is possible to connect a local adb client to a remote adb server (provided they use the same version of the adb protocol).

Indeed I'm not sure Scrcpy can help me to get my goal but I'm sure you know if it can do it or not. What's the truth?
Anyway if Scrcpy can't do this job please tell me if there's a way to get my goal with ubuntu.

---

### Post by TheFu on 2024-09-17
If you want to use your android device to remote into your PC at home, you have to consider network security first.  In general, I only trust 2 methods to do that.
[LIST]
[*]ssh tunnel
[*]VPN tunnel
[/LIST]
That's it. Ain't no other method.  If any tool doesn't use one of those, then I need to force the traffic to use one of those by running the ssh or VPN server at home and running a suitable client (ssh or VPN) on my android device.

I use ssh for all sorts of things both at home and when traveling.  There are remote desktops that include SSH tunneling and authentication built in, but those don't have Android versions.  To me, Android with ssh for remote access it too cumbersome.  sftp is a different thing, though it uses the same authentication and port as normal ssh.  Additionally, sftp is automatically installed and enabled when you install the openssh-server package (or "ssh" meta-package that installs both the client and server stuff for ssh).  ssh is how every computer in the world communicates, except it took MSFT about 25 yrs to realize it, so their implementation came at least 15 yrs too late.  ssh tunnels are for 1 TCP port, not all traffic regardless of port and never for UDP traffic.  If you use ssh over the internet or any ssh-based tools  (there are about 50), then only ssh-keys or ssh-certs should be used for authentication - NEVER passwords.  Even though I don't allow password authentication to my ssh ports over the internet, I see about 5,000 hack attempts daily.  So far today, on a single system, there are 821 failed hack attempts (218 are invalid users, 2509 are trying to use root, which isn't allowed).  Anyway, ssh = cumbersome from Android.  Moving on.

VPNs aren't hard. Running some VPN variants is pretty easy, like Wireguard.  Wireguard is really a peer to peer VPN, but 1 of the devices, somewhere, needs to be available with an open port for inbound connections.  There's also OpenVPN, which is extremely mature and capable, but with those things comes complexity.  Wireguard is simple, almost too simple for good security.  There are hundreds of easy-to-follow guides for running a wireguard VPN server.  The complexity all happens on the server-side.  That's where you'll create the keys used by each client - to place in the server and client config files.  The server config needs to know the public keys for all clients.  A client config file only needs to know it's private key and the server's public key, which means the client config files are short and identical except 2 lines.  There's a tool that will generate a QRcode from the client config file - make 1 qrcode for each client config file (1 per client device).  Load up the wireguard client on android, connect to the local network (or cell data), then load the config file using the QRCode for that client, then toggle the VPN client on or off as you like.  That's it.  Going forward, you just turn it on or off when you like.  I suppose there's a way to have it always on. I don't use it that way.  My elderly Mom was able to understand "on/off".  It really is that easy on the client side, after setup.

Wireguard or openvpn forward everything through the tunnel. All ports, all traffic, everything that isn't specifically excluded through a routing table.

Wireguard performance is much faster than openvpn.  Setup of the tunnel for openvpn takes about 2-3 seconds.  Setup for the tunnel for wireguard is sub-second.  If openVPN throughput is 10 Mbps, then Wireguard throughput is 40Mbps. 

Both Wireguard and openvpn require key-based authentication. Those are built-into both, so there isn't any option.  Nobody even tries to hack wireguard or openvpn unless there is a backdoor bug, never brute force attacks.

Ok, so you choose wireguard as your VPN, setup everything, and connect.  What's next?  Well, your Android devices are on the same subnet as all your other systems, so you do whatever you'd do when at home from android.  Obviously, the network will be slower, but still workable for most people with broadband at home.  When I'm traveling, I'll stream video from my media server at home this way.  I do down transcode to DVD quality when doing this, but streaming my music collection from home is easy.  I avoid using my cell data plain for high bandwidth needs.  I have full access to nextcloud, jellyfin, any storage, and even my VoIP system.  

What I don't do from android?  I don't use remote desktops or try to run GUI programs on computers at home and have the display shown on Android.  I can do that with a laptop running Linux thanks to ssh X11 tunneling.  From a laptop, I have full access to anything on my home network.  That can be using ssh or wireguard for network security.  ssh from a linux laptop no matter where I am, is about the same, just need to understand that the network connection will be slower.  Afterall, wifi from Patagonia back to home isn't the same as my wired GigE ethernet connection using switches either in the same room or across the hall.  I don't really use wifi at home with laptops.

So, you have some choices to make, then a little research/google to do, and perhaps some expectations to manage.

---

### Post by gipsyshadow on 2024-09-17
Well... so many infos, thanks!
I've got this basic smartphone and I opened a new google account just for it, without sensitive informations about me because I'm going to use this phone only to make calls, without registering any of my phone numbers and without installing any app so definitely this phone will be "empty" about my personal informations. Due to that privacy (or... security?) is totally irrelevant in my scenario.
That said let me ask you a very easy/nooby question: is wireguard the best (... and easiest!) way to control my android phone by my pc through the internet via my phone's data internet connection? As said I don't care about privacy/security.
If wireguard could be my best choice, what are its limits? Eg. can I remotely switch off and on my phone? Can I listen to my own phone calls? I'd like to experience all that.

---

### Post by TheFu on 2024-09-17
I think there's some confusion. I probably jumped forward to the solution and assumed you'd already, magically, know all the terms. Sorry.

Wireguard is a VPN.  Whether it is the best or not is subjective.  Whether it is the easiest is also subjective. VPNs are about the network connection between the two systems. It doesn't know anything about remote control.  It doesn't care about the OSes involved.  It is a generic network security and network authentication tool.  It is required for security when going over the internet.   If you don't know what a VPN is, read this: [https://en.wikipedia.org/wiki/Vpn](https://en.wikipedia.org/wiki/Vpn)

Once the VPN is working, it might be possible to use something like [https://kdeconnect.kde.org/](https://kdeconnect.kde.org/) . I've never used it.  I know that Samsung has a similar capability, but not on their low-end devices.  There's also [https://extensions.gnome.org/extension/1319/gsconnect/](https://extensions.gnome.org/extension/1319/gsconnect/) ... but it only works with Gnome, which I don't use. Never tried GSConnect. If you use Gnome, try GSConnect.  If you use KDE or LXQt, try KDEConnect.

To be clear, I've never used either of those and my Samsung tablet is too low-end to use their Connect tool.  

Google is excellent at security, but terrible at privacy.  Privacy and security are very different things, though it is easy to want to group them into one, because we generally want both ... er ... until we learn that something convenient won't work without giving up privacy.

---

### Post by gipsyshadow on 2024-09-18
Ok, I must admit I had a lot of confusion. Now it's a little bit better but tell me an easy thing just to get a safe point to start from: is GSConnect for different things in comparison with scrcpy? I've tried to read something on the web but honestly I couldn't understand their differences.

Another easy question: what are the "elements" I need for my goal? AFAIK just scrcpy (or GSConnect?) + vpn tunnel (as Wireguard), then my desktop pc and my phone with their internet connections of course; is it right?
By the way I've just remembered that I use a 4G internet dongle with a sim card connected via USB to my pc to access the internet; is this important in this scenario?

Let me ask you one more question about ADB in ubuntu. I installed these 4 packages from Synaptic:
```

adb
android-libadb
android-libadb-dev
android-sdk-platform-tools-common

```
just because I searched "adb" and I got those 4 results (sorry if it sounds funny!). Are they the right packages to make Scrcpy to work with adb in ubuntu? As I said my first attempt went quite good because I could only see what I physically did on my phone in Scrcpy but not the vice versa, so I wonder if adb packages could deal with that other than the obsolete 1.25 Scrcpy release.

---

### Post by TheFu on 2024-09-18
Most cell data providers will prevent running a VPN server. It is called Carrier NAT. You can google it. I don't know the other things.

Maybe someone else can rephrase or fill in the blanks for the clarity you seek.

---

