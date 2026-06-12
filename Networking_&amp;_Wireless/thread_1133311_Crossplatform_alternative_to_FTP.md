---
title: "Crossplatform alternative to FTP?"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-04-22
Okay so after failing at [setting up an FTP server in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1079983") I am thinking of a better way since I am told FTP isn't secure (Lots of webhosting places use FTP to upload content, so does that mean sites hosted by them are at risk?).

I am wondering if there is a way I can access files on my Ubuntu machine on a windows computer over the internet? or Vice versa (access Windows from Ubuntu).

It would also be cool if I could stream MP3s right off my computer without having to wait for them to download.

So I basically need something to install on my Ubuntu computer to share the files and something to install on a windows computer to access these files and possible stream them (maybe allow me to map it to a drive in Windows).

---

### Post by abyssius on 2009-04-22
> **RealG187 said:**
> I am wondering if there is a way I can access files on my Ubuntu machine on a windows computer over the internet? or Vice versa (access Windows from Ubuntu).
 
Not without a basic understanding of IP networking (how the Internet works). If you're dwelling on things like is FTP secure or not, then you have some research ahead of you.

---

### Post by RealG187 on 2009-04-23
I am taking a Network+ course. I know how the internet works. The book says something about making a request on a random port to port 21 on the server and the server uses port 20 to connect to a random port back (usually one above the port used to initiate the connection.

---

### Post by mshipman on 2009-04-23
If you're worried about FTP security, try SFTP.

~MS

---

### Post by RealG187 on 2009-04-23
I am not too worried it's just that someone said it's not secure. What would be the easiest and best way to do this?

---

### Post by pytrisss on 2009-04-23
If you want to stream mp3 you would need something like samba. On the windows, just share a folder and in ubuntu connect to it with an IP and folder name.

---

### Post by RealG187 on 2009-04-23
> **pytrisss said:**
> If you want to stream mp3 you would need something like samba. On the windows, just share a folder and in ubuntu connect to it with an IP and folder name.

But I need to do this over the internet, not just a local network.

---

### Post by RealG187 on 2009-04-29
Is there a way I can do this? I wanna be able to upload files to my laptop remotely!

---

### Post by lykwydchykyn on 2009-04-29
By "cross platform" do you mean "works with any OS out-of-the-box" or "can be made to work with any OS with the addition of some free software"?

AFAIK, Windows only supports SMB/CIFS and FTP (and that one poorly) out of the box.  You can do SFTP, which is enabled automatically when you install openssh-server, if you install winSCP on windows.

I've stopped using FTP as much as possible and just use SFTP/SSH for file sharing, especially over the internet.

---

### Post by RealG187 on 2009-04-29
If I could install a piece of software on my Ubuntu laptop and install a piece of software on the windows machine and send files back and forth that would be what I want.

---

### Post by pigphish on 2009-04-29
You can enable samba over a WAN but of course it won't be secure and rather dangerous. The above just involves firewall configurations. In fact that would be true of any service you use in your LAN.

As mentioned SFTP is probably your best bet. It's secure and provides rrobust file handling. Use winscp on windows and ssh on ubuntu.

---

### Post by RealG187 on 2009-04-30
I am not sure if FTP works with my Router.

---

### Post by lykwydchykyn on 2009-04-30
To make sftp work:
 - install openssh-server on the Ubuntu server
 - install winscp on the Windows box
 - open/NAT port 22 on the router

CAVEAT EMPTOR:
If you have ssh open to the web, you WILL have bots/script kiddies trying to brute-force hack it.  That's true of most services to some extent, but ssh is almost guaranteed.  Make sure you install something like fail2ban, do NOT have root login enabled, and use very secure passwords or just key-based logins only (if you only plan to log in with specific machines).

Check this article for a start, if you plan to do this: [http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/](http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/)

---

### Post by RealG187 on 2009-04-30
What is fail2ban?

---

### Post by lykwydchykyn on 2009-04-30
> **RealG187 said:**
> What is fail2ban?

It bans ip addresses after so many failed login attempts.  It's in the repositories.

---

### Post by RealG187 on 2009-04-30
But I cannot even setup FTP, let alone SFTP...

---

### Post by juancarlospaco on 2009-07-23
Secure way:
**SSH**
Insecure Way:
**python -m SimpleHTTPServer**
[I]
Both works on Ubuntu, MAC OS X, and Legacy OS too[/I] :)

---

### Post by bear24rw on 2009-07-23
on ubuntu install openssh-server foward port 22 on your router and then over the internet on a windows machine you can connect using putty and if you want to transfer files tunnel a port and use filezilla to transfer files

---

### Post by RealG187 on 2009-07-23
I tried using DMZ on my computer and I still could not connect, would there be a reason for that?

---

### Post by lykwydchykyn on 2009-07-23
Is your ISP blocking the port?

---

### Post by RealG187 on 2009-07-23
> **lykwydchykyn said:**
> Is your ISP blocking the port?I don't know, how do I find out?

---

### Post by lykwydchykyn on 2009-07-23
> **RealG187 said:**
> I don't know, how do I find out?

Call them up and ask, I guess.

How are you hitting this from the outside?  Do you use a dynamic dns service, or have a static ip, or or are you just using the IP on the router?  

If it works inside but not outside, then the problem is not on the server (unless you've manually made changes to hosts.allow or hosts.deny at some point, which I doubt).

The problem is going to be:
 - router/modem configuration
 - ISP intervention
 - using the correct IP address on the outside.

---

### Post by RealG187 on 2009-07-24
I goto [http://privax.us/ip-test](http://privax.us/ip-test) and use that IP and the ports are forwarded (or I use DMZ) and it doesn't work.

It works for VNC on port 5900...

---

### Post by Matthew Wiebelhaus on 2009-07-25
Hamachi?

---

### Post by RealG187 on 2009-07-26
> **Matthew Wiebelhaus said:**
> Hamachi?I think I heard of that. That's a VPN right?

Hmmmm, if I get that I could just use Samba and could copy or stream data! Is it secure to do this?

Would Hamachi work on Ubuntu and Windows?

---

### Post by martinbaselier on 2009-07-26
Hamachi is dead easy on windows and they have a linux version too, which is commandline only. Hamachi uses an encrypted connection to connect. When only using windows, it's one of the easiest setups you can create. On linux it's only a little harder, missing the gui.

---

### Post by RealG187 on 2009-07-26
So would it create a new Network Connection and a new inferface (ethx) in Ubuntu and act like a local network?

How do I set it up?

---

