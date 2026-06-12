---
title: "Application firewall similar to ZoneAlarm?"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by supaneko on 2008-12-11
One issue I have had since my switch to Ubuntu two years ago is the lack of a graphical application firewall. Now, I understand that I may not be using the proper terminology to describe this so I thought I may need to provide a bit of clarification.

On my old Windows PC's, I always installed ZoneAlarm for my firewall. What was great about this program was that I could set individual application settings via its graphical interface. When a program installation would begin and it wanted to phone home, I could easily block it. When a program wanted to check for updates constantly, it would alert me and I could easily choose to allow or deny its network access.

Where is this feature in Ubuntu? Where is this feature in any Linux distro for that matter?

I have seen AppArmor, somewhat. I had high hopes that this would be the end of my search but I have quickly discovered that this is likely not what I am looking for. There is no intuitive graphical interface that I can use.

I am dying to have a program to set individual settings for network access for each application I have running on my PC. I know that there are programs on here that like to phone home, I know that there may be other programs doing all sorts of questionable network activity and I would like to have the option to prevent that.

Any ideas? :)

---

### Post by 2hot6ft2 on 2008-12-11
System>Administration>Firestarter go thru the simple setup

---

### Post by grantk86 on 2008-12-11
> **2hot6ft2 said:**
> System>Administration>Firestarter go thru the simple setup

You can also install gufw (this is a graphical interface to UFW).  It is easier to setup and use than Firestarter and provides nearly the same functionality.

I don't believe there is a program that will allow you to allow/deny access for specific applications, but you can easily setup the firewall to, by default, allow or deny incoming/outgoing traffic, and then add port exceptions.  There are also some built in "service exceptions" that will open the default ports for services like SMTP, SSH, and Samba.

---

### Post by supaneko on 2008-12-11
OK........ I knew that I should have mentioned that I have already tried Firestarter in my original post.

Firestarter is great for customizing the firewall that comes with Linux. When I want to block a port, allow a port, or grant and deny access based on the device it works just as expected. But that's it... I have not seen any additional functionality with Firestarter to do what I have seen in ZoneAlarm. Firestarter has not been updated in ages it seems as well. It comes with a few bugs where it likes to crash more often than stay active and display itself on my system.

I am specifically looking for a program that will allow me to control the network access of individual programs. I have no way of blocking just simple ports because most of the programs that phone home seem to do so through port 80. I'm sure we all know what will happen if I block port 80. :)

I was under the impression that AppArmor provided this functionality. The catch to it is that you must setup rules and profiles through the command line. I suppose I would not require a GUI if there was a decent tutorial or guide somewhere that explained in basic terms how to configure it. :(

---

