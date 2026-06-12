---
title: "Downlowding Maverick with a firewall in the distribution package?"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by dareys on 2012-10-27
Greetings,

I am currently using a wireless connection that is surely exposed to hackers. I have complained about it on this forum before.

My Windows network drivers are shot and in spite of downloading and re-installing then several times, I still can´t access the network. No answers from Lenovo or Microsoft yet.

I have created a boot USB drive with UBUNTU on it. However, in spite of changing the ubuntu and root passwords, and installing gufw the firewall, I still have to re-install twice a week. 

The problem is that I am missing a security step or I am getting hacked while I download and install gufw...

Where can i download a version of Ubuntu 10.4 Maverick with gufw in the distribution disk? I have not downloaded the newest versions of Ubuntu because I can´t access xterm and stuff. Hidden

Your help would be appreciated.

Regards,

Jean-Pierre

---

### Post by cwsnyder on 2012-10-27
If your wireless connection is exposed to hackers, changing ANYTHING on your computer is not going to work.  You first need to activate the firewall on your wireless router and implement WPA-PSK (a.k.a. WPA2) encryption on all communication with the router.  If this breaks some of your toys because they can't be coerced to send a passkey to the router to connect, that is the price of security.  You can either be secure, or you can be open, being both isn't possible.  If your router is not under your control, my sympathy, but no solution.  If your router doesn't have a firewall or capability to support modern wireless encryption, replace it.

---

### Post by dareys on 2012-10-27
> **cwsnyder said:**
> If your wireless connection is exposed to hackers, changing ANYTHING on your computer is not going to work.  You first need to activate the firewall on your wireless router and implement WPA-PSK (a.k.a. WPA2) encryption on all communication with the router.  If this breaks some of your toys because they can't be coerced to send a passkey to the router to connect, that is the price of security.  You can either be secure, or you can be open, being both isn't possible.  If your router is not under your control, my sympathy, but no solution.  If your router doesn't have a firewall or capability to support modern wireless encryption, replace it.

Greetings,

No. The router is not under my control. And even if I had a crack at configuring it, I might break the owner´s toys...

So, I am trying to pick up the wireless signal from the owner´s router with a router of my own, which would be under my control.

I would configure it for WPA2 encryption and publish the signal from a non published SSID whose name only I would know.

Would that work? 

Thank you for the response.

Jean-Pierre

---

### Post by jerome1232 on 2012-10-27
Ubuntu has UFW installed by default, what is wrong with that?

Define what you mean by "you are getting hacked"

---

### Post by dareys on 2012-10-27
> **jerome1232 said:**
> Ubuntu has UFW installed by default, what is wrong with that?

Define what you mean by "you are getting hacked"
Greetings,

Ok, I will look for UFW. It might not be enabled. And if it is, it is useless. They still get through. 

Hacked, well, my list is huge:

- People write me emails and if I get them, they disappear from my
  inbox before I can read them. So I write again, and people respond with 
  timestamped copies of the originals they sent me. Sometimes rather upset. Changing my passwords doesn´t change it.
- My passwords to sites like Ubuntu, Microsoft, Lenovo, HP don´t work
  more than once. I set them to the same thing and they reset themselves
  I have to request new ones almost every time.
- My sessions freeze continuously. 
- I loose functionality on the OS, like all of a sudden I can no longer 
  use the track pad, but the mouse works.
- I suddenly no longer can connect to the network.
- I open my mail and all of a sudden messages I did not click on 
  are opened.
- Web pages I did not ask for open. When I click on a page I want another
  appears.
- Suddenly web pages loose funcionality. Buttons are greyed out or no
  longer there.
- I type x and I get y. The text, size, colour and font of 
  messages I write changes spontaneously...

and I have tons of other complaints... Just no time now.

The point is that if I re-install the OS, everything works again, at least for a while. So, are Windows and Ubuntu self destructing OSs? I doubt it. But I never had these problems with HP-UX, IBM-AIX or SUN Solaris. 

Regards,

Jean-Pierer

---

### Post by cwsnyder on 2012-10-28
I think you would be better off getting your own Internet connection.  Connecting to someone else's WiFi, you will always be subject to keylogging, packet sniffing, and other problems from _their_ connection.  That is the reason why it is recommended that you don't use public WiFi connections for anything secure.

Unfortunately, anything you do on your end can't secure what is open between you and the Internet.

---

### Post by dareys on 2012-10-29
cwsnyder,

Thank you for the response. You are 100% right. Using somebody 
else´s signal, regardless of what I do with my modem, still leaves me exposed.

The point is, I would have many of the same problems with my own connection.

The guys that install it down here in Mexico, don´t exactly spend a lot of time securing the network... and all protocols are hackable. WEP, WPA, WPA2 etc.

Suggestions?

Perhaps 

Regards,

Jean-Pierre

---

### Post by jerome1232 on 2012-10-29
Actually wpa is pretty dang hard to crack, provided you are using a long complicated passphrase that is not in a dictionary. 

The best WPA-PSK cracker can check 100 PSKs (pre shared keys) per second on a very fast PC. Assuming you don't use a pasword found in a dictionary, you have to brute force the key, a key 10 characters long would take 579,299 years to crack with a single fairly fast personal computer. 

It's simply not feasible for a person to crack wpa on a home network in any feasible amount of time, use a strong password not in a dictionary that is fairly long.

---

### Post by dareys on 2012-10-29
> **jerome1232 said:**
> Actually wpa is pretty dang hard to crack, provided you are using a long complicated passphrase that is not in a dictionary. 

The best WPA-PSK cracker can check 100 PSKs (pre shared keys) per second on a very fast PC. Assuming you don't use a pasword found in a dictionary, you have to brute force the key, a key 10 characters long would take 579,299 years to crack with a single fairly fast personal computer. 

It's simply not feasible for a person to crack wpa on a home network in any feasible amount of time, use a strong password not in a dictionary that is fairly long.

Thank you for confirming what I have found out and quantifying. The figures are reassuring. 

The point then is to use long strings of completely random characters and numbers, nothing that can be found in a dictionary, encyclopedia, in any known language. 

I have heard that hackers customize huge dictionnaries.

---

### Post by dareys on 2012-10-29
However, you have heard of parallel computing right? Or what hackers do stealing CPU cycles from machines worldwide that are left on and connected to the network at night right? So, a single person, perhaps not, but a really good hacker, or network of hackers, and I am sure you can crack a home based WPA key. Hey, and what if the hacker is the government? Then, well, you are toast. And big brother is watching you know! LOL:

---

### Post by jerome1232 on 2012-10-29
Sure, a cloud of super computers could do it. You would need hundreds of personal computers working in parallel to do it. Change your password once a month if you're worried about that.

---

### Post by dareys on 2012-10-30
> **jerome1232 said:**
> Sure, a cloud of super computers could do it. You would need hundreds of personal computers working in parallel to do it. Change your password once a month if you're worried about that.

>However, you have heard of parallel computing right? Or what >hackers do stealing CPU cycles from machines worldwide that are >left on and connected to the network at night right? So, a >single person, perhaps not, but a really good hacker, or network >of hackers, and I am sure you can crack a home based WPA key. >Hey, and what if the hacker is the government? Then, well, you >are toast. And big brother is watching you know! LOL:

Worried about it? You bet. I would have to change my password daily, and even then. Recently I have been monitoring when and where my email account is opened. 

And while I was in the USA two weeks ago, my Yahoo email was opened in the USA and Mexico on the same day last week... So, I suspect it is network sniffing of the IP address from where I work. Easy to spot once I open a trigger email right? Anyway, yes, I will be changing my password more often. I now have about five ways to retrieve it, so I am not as worried. Thank you for the head up.

---

### Post by jerome1232 on 2012-10-30
Someone shouldn't be able to sniff your login credentials, all logins to email should be encrypted. Even if you were on an open WiFi connection and everyone around you could sniff your traffic, the login credentials you use to login to webmail would be encrypted.

If you were using a Windows computer I would say you have been keylogged or other eavesdropping malware is nabbing your password. Do you ever login to your email from public computers?

---

### Post by dareys on 2012-10-30
> **jerome1232 said:**
> Someone shouldn't be able to sniff your login credentials, all logins to email should be encrypted. Even if you were on an open WiFi connection and everyone around you could sniff your traffic, the login credentials you use to login to webmail would be encrypted.

If you were using a Windows computer I would say you have been keylogged or other eavesdropping malware is nabbing your password. Do you ever login to your email from public computers?

Thank you for the help. Now we are narrowing down on the issue. 

My Windows PC network drivers were somehow blown away and I have been unable to restore them. Close but no cigar and lack of time... So, I have not been logging in from my Windows installation.

I created an Ubuntu bootable USB and I use that to connect to the network. It gets blown away daily. Gufw is not enough to protect me. So, I re-format it daily. Unless the source code is tampered with that should be clean. And when I use a fresh install, and change the password, I still experience the hacking.

Otherwise, I use an internet place that I believe is good. No wifi, avast anti-virus and firewall running windows. It could happen both places.

However, no, I was in Las Vegas at a Trade Show two weeks ago, and using only fresh Ubuntu installs, and I would get messed up. The keyboard would stop working, or the mouse, or hability to connect to the network, and all the other issues.

So, I think it comes most probably from the network when I am using Ubuntu. Perhpas I should download a fresh version of the Ubuntu distribution?

---

