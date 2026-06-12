---
title: "Connect to Wifi Network Prior to User Login:"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by nbotticelli on 2010-04-29
Hello!

I am setting up netbooks running Edubuntu 9.10 for my sixth grade students. The machines will be joined to an Active Directory server as of part a Server 2003 Domain.

I can get accounts to login fine with the regular AD credentials if the computer is connected with an ethernet cable.

For wireless though I have to login as local admin account where it will then connect to the wireless network that I have created then I have to log off the local account and I can then login with the AD credentials because the computer remains connected to the wifi network even after you have logged off the local account.

The wifi network is set to be connected to automatically and to be available to All Users.

I am using likewise-open 5.0XXX to join the machines to the domain which is what is available through the repositories. I noticed that 5.3 is available from their website but it doesn't seem to want to install plus I'd rather go with what is in the repos anyway.

Supposedly likewise-open should still at least login a user that has already logged in at least once before in case the DC goes offline. You would think this would apply to the computer not being connected to the network quite yet too.

Any ideas?

Is there a way to force Ubuntu to connect to a specified network prior to a user logging in?


Thanks!

---

### Post by nbotticelli on 2010-04-30
Any ideas?

---

### Post by pwebster25 on 2010-05-04
nbotticelli-
You may have figured this out already but this is what I would recommend.  Make sure the check box is marked "yes" for "connect automatically" and "available to all users" when you edit the wireless connections that will be used.  This seems to make the difference for me. I came across your problem while looking for a solution for my own.

My own machine logs in now with AD credentials in a wireless setting.  However, I can't use my AD credentials when I am away from the domain.  I should be able to do this.  I used to be able to before upgrading to Lucid.

---

### Post by nbotticelli on 2010-05-05
I did have both checked off. Strangely though they've started to connect prior to logging in now.

Still no AD credentials caching properly though.

---

### Post by pwebster25 on 2010-05-05
Interesting.  I wish that would magically happen to me. Did you figure out what might have made the difference?

---

### Post by yvovandoorn on 2010-05-10
Are you both experiencing this with 10.04 or 9.10?
If you do '/opt/likewise/bin/lw-get-status | grep VERSION', what does it return?

Cached credentials should be working reliably in 5.4, so I am a bit concerned that you two are seeing something different. 

Yvo

---

### Post by pwebster25 on 2010-05-10
> **yvovandoorn said:**
> $If you do '/opt/likewise/bin/lw-get-status | grep VERSION', what does it return?

This is what I did.  I am running 10.04. It seems to be missing some key files for likewise or maybe it put them in an unusual place.  I did have 9.10 on this same machine and ran an upgrade.  I, then, uninstalled and then reinstalled likewise 5.4.

```
$ /opt/likewise/bin/lw-get-status | grep VERSION
bash: /opt/likewise/bin/lw-get-status: No such file or directory
```

In fact, I navigated to /opt in Nautilus (w/ sudo gksudo nautilus) and found that I don't have a folder there called /opt/likewise/ .  I only have /opt/Adobe/ and /opt/google/

Is /opt/ the right location for likewise 5.4.  If so, then that might explain why things don't work.

---

### Post by yvovandoorn on 2010-05-11
Yes, /opt/likewise is where Likewise is installed. Ubuntu hass symlinks to it from /usr/bin but the actual binaries live in that dir.

I'd recommend to force a reinstall of Likewise and give it another shot.

---

### Post by yvovandoorn on 2010-05-12
So I was a bit wrong. I spoke with one of our developers who told me for Ubuntu we actually install our binaries to /usr/bin, not /opt/likewise like we do when you download from likewise.com

Could you please run:

/usr/bin/lw-get-status to see what the current status of your join is?

---

### Post by pwebster25 on 2010-05-13
Thanks-
You are right.  It is in /usr/

I did the following (with results edited to protect security):
```
$ /usr/bin/lw-get-status
LSA Server Status:

Compiled daemon version: 5.0.0.0
Packaged product version: 5.4.0.42111
Uptime:        0 days 13 hours 6 minutes 46 seconds

[Authentication provider: lsa-activedirectory-provider]

	Status:        Online
	Mode:          Un-provisioned
	Domain:        myDOMAINname.DOMAIN
	Forest:        
	Site:          
	Online check interval:  300 seconds
	[Trusted Domains: 1]


	[Domain: MSD]

		DNS Domain:       mydomainname.domain
		Netbios name:     MYDOMAINNAME
		Forest name:      mydomainname.domain
		Trustee DNS name: 
		Client site name: 
		Domain SID:       A Bunch of numbers and letters
		Domain GUID:      A Bunch of numbers and letters
		Trust Flags:      [0x001d]
		                  [0x0001 - In forest]
		                  [0x0004 - Tree root]
		                  [0x0008 - Primary]
		                  [0x0010 - Native]
		Trust type:       Up Level
		Trust Attributes: [0x0000]
		Trust Direction:  Primary Domain
		Trust Mode:       In my forest Trust (MFT)
		Domain flags:     [0x0003]
		                  [0x0001 - Primary]
		                  [0x0002 - Offline]

[Authentication provider: lsa-local-provider]

	Status:        Online
	Mode:          Local system

```

FYI, I am currently at home and not logged in to my domain.  I am on a local admin level account.

---

