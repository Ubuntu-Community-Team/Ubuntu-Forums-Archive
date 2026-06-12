---
title: "Mac Trojan?"
date: 2009-01-23
forum: Mac OSX
---

### Post by Sealbhach on 2009-01-23
It says 20,000 Mac users have got this thing.

[http://www.crn.com/security/212902066](http://www.crn.com/security/212902066)

I was wondering how much damage can it do, given that OS X is supposed to be very secure. Is this the future for Linux too?


.

---

### Post by Person8880 on 2009-01-23
> **Sealbhach said:**
> It says 20,000 Mac users have got this thing.

[http://www.crn.com/security/212902066](http://www.crn.com/security/212902066)

I was wondering how much damage can it do, given that OS X is supposed to be very secure. Is this the future for Linux too?


.
Well to be affected by this trojan you have to:
1. Be stupid enough to trust torrents and pirated software.
2. Be stupid enough to grant said software administrator access using your password.
3. Be ignorant and believe OS X has no threats to it.

Then once you have done the above, a hacker has root access to OS X to do with it what he wishes, which basically means your screwed.

---

### Post by tsali on 2009-01-23
> **Sealbhach said:**
> It says 20,000 Mac users have got this thing.

[http://www.crn.com/security/212902066](http://www.crn.com/security/212902066)

I was wondering how much damage can it do, given that OS X is supposed to be very secure. Is this the future for Linux too?


.

Yes it is the future of linux as more and more users adopt it.

It would be somewhat mitigated by providing a broad choice of software in the repo so that users wouldn't be tempted to install mysteryware from sketchy sources.

Just imagine the impact of "Photoshop for Linux" on a bittorrent site...

---

### Post by jeyaganesh on 2009-01-24
Yes, linux especially Ubuntu may be target of hackers in near future because of its popularity.

---

### Post by NoSmokingBandit on 2009-01-24
> **jeyaganesh said:**
> Yes, linux especially Ubuntu may be target of hackers in near future because of its popularity.

You *are* aware that the market share for Ubuntu is not even comparable to osx's, right? Ubuntu will need a lot more users than it has now if you think market share plays a role in this.

---

### Post by Frak on 2009-01-24
I've seen this in my shop. About ten Mac users have come in and have had this bug detected on their machine.

Though, all of these were from Limewire downloads.

---

### Post by tsali on 2009-01-25
> **NoSmokingBandit said:**
> You *are* aware that the market share for Ubuntu is not even comparable to osx's, right? Ubuntu will need a lot more users than it has now if you think market share plays a role in this.

The key concept at work here is that greater popularity of a product means that there will be a greater slice of "casual" users that aren't as careful with security habits as hardcore users.

Ubuntu has made it easier for casual users to come to linux. Even with a lower market share, it is expanding and that expansion includes these folks.

*nix trojans are easy enough to write. What makes them easy is how simple it is to manipulate the casual consumer user into providing the root or administrator password. Just as has been done with this Mac trojan.

In the past, a big component of *nix security has been that *nix systems were often large scale educational or enterprise affairs with trained administrators and limited user accounts. 

In consumer systems, the admin and user are usually the same person. When the "user" wants to install a new program, he's free to do so, unlike those aforementioned professionally administered systems.

---

### Post by 3rdalbum on 2009-01-26
There are heaps of ways for trojans run as limited user on OS X to gain root access without a password. Some are Apple programming errors and could be patched if Apple cared, but some are bad design choices that ALL Macintosh programs depend on, and as such are set in stone and irrepairable.

I'm not aware of any security flaws on Ubuntu that result in root access without a password.

Ubuntu FTW.

---

### Post by cardinals_fan on 2009-01-26
> **3rdalbum said:**
> 
I'm not aware of any security flaws on Ubuntu that result in root access without a password.

There is a rather major design flaw that allows root access *with* a password - a cocky user in the chair behind the screen.

---

### Post by 3rdalbum on 2009-01-26
> **cardinals_fan said:**
> There is a rather major design flaw that allows root access *with* a password - a cocky user in the chair behind the screen.

That is, assuming the cocky user has sudo access :-)

---

### Post by Demio on 2009-01-26
> **3rdalbum said:**
> There are heaps of ways for trojans run as limited user on OS X to gain root access without a password. Some are Apple programming errors and could be patched if Apple cared, but some are bad design choices that ALL Macintosh programs depend on, and as such are set in stone and irrepairable.

I'm not aware of any security flaws on Ubuntu that result in root access without a password.

Ubuntu FTW.
Really? Care to show us some examples then?

I'm interested about all the root-obtainability exploits in Mac OS X that haven't been published and fixed and about which I never heard off.

---

### Post by lisati on 2009-01-26
It's ALWAYS a good idea not to trust stuff from "unknown" sources until you've scanned it for malware. And that's quite apart from protecting yourself from potential legal hassles..... And how many of us have "accidentally" installed unwanted extra stuff by clicking on "next" without actually reading what the installer is telling us?

---

### Post by Frak on 2009-01-26
> **Demio said:**
> Really? Care to show us some examples then?

I'm interested about all the root-obtainability exploits in Mac OS X that haven't been published and fixed and about which I never heard off.
As an example, there was a bug back in early 10.4 that allowed a person to obtain root just by going into the Directory Access and clicking on some stuff (I won't go into detail, because some Macs still aren't patched against it).

While it's been fixed, there are still some errors out there that can give a person root access without the password.

---

### Post by Demio on 2009-01-26
> **Frak said:**
> As an example, there was a bug back in early 10.4 that allowed a person to obtain root just by going into the Directory Access and clicking on some stuff (I won't go into detail, because some Macs still aren't patched against it).

While it's been fixed, there are still some errors out there that can give a person root access without the password.
I'm talking about vulnerabilities in the latest Leopard 10.5.6. 

I could talk **** all day about Window's past vulnerabilities.
Even the Linux Kernel has had its share of root-obtaining vulnerabilities.

So unless you show me something new, you have nothing but FUD.

---

### Post by Frak on 2009-01-26
> **Demio said:**
> I'm talking about vulnerabilities in the latest Leopard 10.5.6. 

I could talk **** all day about Window's past vulnerabilities.
Even the Linux Kernel has had its share of root-obtaining vulnerabilities.

So unless you show me something new, you have nothing but FUD.
It was an example. If there was a problem in the past, then there will be a problem in the future. There are vulnerabilities known in-house by Apple that can cause root access time without authentication.

To gripe about not connecting the past to future shows inexperience.

---

### Post by Demio on 2009-01-26
> **Frak said:**
> It was an example. If there was a problem in the past, then there will be a problem in the future. There are vulnerabilities known in-house by Apple that can cause root access time without authentication.

To gripe about not connecting the past to future shows inexperience.
But of course! Your logic is rock-solid!!!

Obviously Mac OS X has a ton of root vulnerabilities which we don't know about, and I bet the Apple engineers know all about them and simply won't fix them out of spite towards their user-base. 

Let me use your logic for a bit:
Since the Linux Kernel has had root vulnerabilities in the past, then it will have root vulnerabilities in the future. I bet Linus knows quite a few except he's not willing to share them. And I even bet that they're so well hidden inside the Kernel, no one else will ever notice them!

Now in all seriousness, it's said that there's a bug for each 5000 lines of code. There are bugs in Mac OS X, as there are bugs in Linux. There might even be root exploits somewhere in the Mac OS X code, as they also might exist in the Linux code. No codebase is perfect, and the only 100% bug-free software is "Hello World." But does this make Mac OS X or Linux inherently insecure? Obviously not, this kind of bug is very rare and is usually fixed ASAP after it's found.

Now please stop spreading FUD ;)

---

### Post by Frak on 2009-01-26
> **Demio said:**
> Now please stop spreading FUD

Stop your hyperbole's and listen to somebody qualified on this topic.

Microsoft does the same thing, along with Novel and RedHat. They find bugs in software, but don't release the bug for security reasons. How would it help if they couldn't fix the software in time, but find it crucial to essentially tell everybody how to abuse it.

Oh, and quit trying to prove people wrong by exaggerating the topic to the other extreme. It makes you look bad ;)

---

### Post by Demio on 2009-01-26
> **Frak said:**
> Stop your hyperbole's and listen to somebody qualified on this topic.

Microsoft does the same thing, along with Novel and RedHat. They find bugs in software, but don't release the bug for security reasons. How would it help if they couldn't fix the software in time, but find it crucial to essentially tell everybody how to abuse it.

Oh, and quit trying to prove people wrong by exaggerating the topic to the other extreme. It makes you look bad ;)
Edit: KiwiNZ is right. I should have never replied to your personal attacks.

Have a good day :)

P.S.: You still have no proof about your wild claims. While there's a chance that there might be a permissions escalation exploit in Mac OS X, it's very unlikely, as this kind of bugs is very rare on *NIX based operative systems. Buffer overflows that lead to code execution? There are probably quite a few of those lying around, but root exploits? Unlikely.

---

### Post by KiwiNZ on 2009-01-26
OK back to the neutral zones gentlemen.
Don't make the discussion personal .If it continues this way I will close the thread.

---

### Post by handy on 2009-01-26
It seems to me no matter what the OS, a trojan is by its very nature the form of infiltration that is most likely to make it onto the system's drive.  If the software that it is hiding in requires a root password for installation, then it is in, & most likely now has root access.

This kind of mal-ware is also most likely to spread the way that this current Mac trojan is.  As it needs to come in, in very popular illegal software, for the Mac's anyway.  For Linux, the chances of this happening are far slimmer, as there is very little software that is not free, open & therefore vetted by the community.

I think this Mac trojan is a storm in a tea cup.

---

### Post by Demio on 2009-01-26
> **handy said:**
> It seems to me no matter what the OS, a trojan is by its very nature the form of infiltration that is most likely to make it onto the system's drive.  If the software that it is hiding in requires a root password for installation, then it is in, & most likely now has root access.

This kind of mal-ware is also most likely to spread the way that this current Mac trojan is.  As it needs to come in, in very popular illegal software, for the Mac's anyway.  For Linux, the chances of this happening are far slimmer, as there is very little software that is not free, open & therefore vetted by the community.

I think this Mac trojan is a storm in a tea cup.
Well said.

---

### Post by Frak on 2009-01-26
> **Demio said:**
> Edit: KiwiNZ is right. I should have never replied to your personal attacks.

Pot calling the kettle black.

> **Demio said:**
> P.S.: You still have no proof about your wild claims.

[http://www.securemac.com/macosxsetuidroot.php](http://www.securemac.com/macosxsetuidroot.php)

> **handy said:**
> It seems to me no matter what the OS, a trojan is by its very nature the form of infiltration that is most likely to make it onto the system's drive.  If the software that it is hiding in requires a root password for installation, then it is in, & most likely now has root access.

This kind of mal-ware is also most likely to spread the way that this current Mac trojan is.  As it needs to come in, in very popular illegal software, for the Mac's anyway.  For Linux, the chances of this happening are far slimmer, as there is very little software that is not free, open & therefore vetted by the community.

Aye, there's a distinct difference between the people using Linux and those using OS X. The Linux crowd is, usually, more security minded and not as likely to let anything execute a super user command as those who think they need to, to get that *thingie* to work.

> **handy said:**
> I think this Mac trojan is a storm in a tea cup.

Aye.

---

### Post by Demio on 2009-01-26
> **Frak said:**
> Pot calling the kettle black.
I wont reply to provocations :)
> **Frak said:**
> 
[http://www.securemac.com/macosxsetuidroot.php](http://www.securemac.com/macosxsetuidroot.php)


Err, that bug is old and has been fixed for a long time:
 - Operating System: Max OS X Version Affected: up to 10.1
 - Fixed: 10.20.2001 see below

I never denied the existence of  permissions escalation bugs in the past, but the number of permissions escalation exploits has been scarce and they've almost always been fixed in a timely manner  ;)

A few Linux-related ones:
[http://www.gentoo.org/security/en/glsa/glsa-200808-12.xml](http://www.gentoo.org/security/en/glsa/glsa-200808-12.xml)
[http://xforce.iss.net/xforce/xfdb/32597](http://xforce.iss.net/xforce/xfdb/32597)
[http://www.isec.pl/vulnerabilities/isec-0013-mremap.txt](http://www.isec.pl/vulnerabilities/isec-0013-mremap.txt)
[http://secunia.com/advisories/10328/](http://secunia.com/advisories/10328/)

Does this make Linux an inherently bad or insecure kernel, or Gentoo an inherently bad or insecure distro? Not by a long shot :)

---

### Post by Frak on 2009-01-26
> **Demio said:**
> I wont reply to provocations :)


Err, that bug is old and has been fixed for a long time:
 - Operating System: Max OS X Version Affected: up to 10.1
 - Fixed: 10.20.2001 see below

I never denied the existence of  permissions escalation bugs in the past, but the number of permissions escalation exploits has been scarce and they've almost always been fixed in a timely manner  ;)

A few Linux-related ones:
[http://www.gentoo.org/security/en/glsa/glsa-200808-12.xml](http://www.gentoo.org/security/en/glsa/glsa-200808-12.xml)
[http://xforce.iss.net/xforce/xfdb/32597](http://xforce.iss.net/xforce/xfdb/32597)
[http://www.isec.pl/vulnerabilities/isec-0013-mremap.txt](http://www.isec.pl/vulnerabilities/isec-0013-mremap.txt)
[http://secunia.com/advisories/10328/](http://secunia.com/advisories/10328/)

Does this make Linux an inherently bad or insecure kernel, or Gentoo an inherently bad or insecure distro? Not by a long shot :)
But does that mean that it is infinitely secure? No, it actually reinforces that it is not. This is what I've been trying to explain this entire time if you would have just listened and quit trying to preach that I'm spreading FUD.

---

### Post by cardinals_fan on 2009-01-26
> **3rdalbum said:**
> That is, assuming the cocky user has sudo access :-)
Indeed.
> **Demio said:**
> But of course! Your logic is rock-solid!!!

Obviously Mac OS X has a ton of root vulnerabilities which we don't know about, and I bet the Apple engineers know all about them and simply won't fix them out of spite towards their user-base. 

This is obviously not true, but Apple does have a rather disturbing (to me) history of putting marketing above all else.  I don't really like their "You can trust us, so we won't tell you much about our security" policies.

[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9111398&source=rss_topic17](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9111398&source=rss_topic17)
[http://blog.ncircle.com/blogs/sync/archives/2008/08/apple_dns_patch_fails_to_rando.html](http://blog.ncircle.com/blogs/sync/archives/2008/08/apple_dns_patch_fails_to_rando.html)
[http://www.macworld.com/article/134793/2008/08/apple_dns.html?t=232](http://www.macworld.com/article/134793/2008/08/apple_dns.html?t=232)

---

### Post by Demio on 2009-01-26
> **Frak said:**
> But does that mean that it is infinitely secure? No, it actually reinforces that it is not. This is what I've been trying to explain this entire time if you would have just listened and quit trying to preach that I'm spreading FUD.
I never said Mac OS X was infinitely secure. 

If you hadn't come in guns blazing talking about stuff that was out of context in relation to my original post, this discussion would have never happened ;)

Please read my original post and the post I quoted in it: [http://ubuntuforums.org/showpost.php?p=6621415&postcount=11](http://ubuntuforums.org/showpost.php?p=6621415&postcount=11)

---

### Post by Demio on 2009-01-26
> **cardinals_fan said:**
> This is obviously not true, but Apple does have a rather disturbing (to me) history of putting marketing above all else.  I don't really like their "You can trust us, so we won't tell you much about our security" policies.

[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9111398&source=rss_topic17](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9111398&source=rss_topic17)
[http://blog.ncircle.com/blogs/sync/archives/2008/08/apple_dns_patch_fails_to_rando.html](http://blog.ncircle.com/blogs/sync/archives/2008/08/apple_dns_patch_fails_to_rando.html)
[http://www.macworld.com/article/134793/2008/08/apple_dns.html?t=232](http://www.macworld.com/article/134793/2008/08/apple_dns.html?t=232)

You are right, Apple's track record about transparency in relation to security isn't the best. I never said Apple was perfect or flawless. 

I was merely arguing that [this post]("http://ubuntuforums.org/showpost.php?p=6618206&postcount=8") lacked sufficient proof to make the wild claims it does.

---

### Post by cardinals_fan on 2009-01-26
> **Demio said:**
> You are right, Apple's track record about transparency in relation to security isn't the best. I never said Apple was perfect or flawless. 

I was merely arguing that [this post]("http://ubuntuforums.org/showpost.php?p=6618206&postcount=8") lacked sufficient proof to make the wild claims it does.
Ah, I see now.

---

### Post by KiwiNZ on 2009-01-26
closed

---

