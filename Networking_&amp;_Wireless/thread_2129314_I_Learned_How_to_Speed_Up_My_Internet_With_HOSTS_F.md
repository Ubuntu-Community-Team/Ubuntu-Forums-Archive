---
title: "I Learned How to Speed Up My Internet With HOSTS File Entries"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by ac5jw on 2013-03-25
Hey, I had a problem over the past three years with my computer taking forever to resolve URLs.  I recently learned how to change DNS servers in Ubuntu 12.04 LTS, but I still had the same delays.  I noticed a marked improvement after several hours with the new DNS provider, but I began to study about creating a HOSTS file from scratch as a means to do domain and host name blocking for uninvited advertisements.

I started with a basic entry for my email provider and for my online banking, and tested it immediately.  I had to learn how to display the original HOSTS file so I could copy anything important to my own version.  I learned about vi /etc/hosts and used my mouse to select the contents and save them elsewhere.

Then I did the hard part, which was to install my HOSTS version using the sudo mv command.  I had trouble following the directory structure to locate my file because I am new to the CLI Terminal.  I ended up saving my NewHOSTS.txt file to my Desktop and I used CLI Terminal to move it from there to the /etc/hosts.  I was pleasantly surprised that my test file with only a couple of entries worked the first time.  But I had a lot to learn about the power of the HOSTS file to speed up my linking, and redirecting, and handovers.  I began to catalog all the URLs I saw in my web browser address bar and then I added the host names to my HOSTS file.  It was like a snowball effect where I was clicking around a lot faster and getting quicker display results.  Even websites not listed in my HOSTS file began to appear more quickly as well.

I also added to my HOSTS file my DNS servers (for practice) and even all of the Mozilla Firefox support domains and hosts.  Now when I click the Help section in Firefox, I get near instant results and there is no waiting for resolution of URLs.

Then at some point I realized that I could do the same thing with the Ubuntu Forums and the Ubuntu servers for downloading updates.  I had to figure out how to get all the names, so I tried looking at the Update Manager process and made it search for updates.  I was able to get some host and domains from that, but there was another place I tried and then I had enough to work with.  Maybe I was using the CLI Terminal to do the apt-get update and saw more of the Ubuntu host server names there.  I noticed immediate results with faster Update Manager, faster CLI Terminal update search, and even the Ubuntu Software Center appears to be displaying faster.

I did my HOSTS file from data I gleaned using the nslookup command in the CLI Terminal.  I was able to get IP addresses and I even noticed some useful data to include, like aliases to the IP address and host names.  After about a week, I have built up a HOSTS fie to the size of just under 700 KB.  It will still fit nicely on a floppy disk.

I like the fact that the HOSTS file is portable.  I can place it in cloud storage for emergency recovery or on a thumb drive for local recovery or backup purposes.

Because I had the primary purpose of blocking unwanted domains and host names, I did a lot of that early on, using data I collected earlier on host names and domains I did not want.  I learned quickly about the 127.0.0.1 address for the unwanted domains.  But when I began to move away from blocking and on to connecting without the wasted time of DNS and delays for service, I focused on the places I visit often or want to visit.  I catalogued many websites that would be of use to me.  I listed my email servers, my cloud storage, my elected officals and the major branches of local, county, state, and federal government, and I had a fun time getting to know the HOSTS file and have practical exercise with creating and storing and moving the HOSTS file.

I have already done the work for speeding up my connections on Ubuntu 12.04 for my DSL modem.  If anyone would like to see the data on Ubuntu servers or on Mozilla Firefox Support, let me know and I will post those sections from my HOST file here in this thread for all to use.

---

### Post by HackerFinn on 2013-03-26
This sounds pretty cool. :) Thank you for the tip. :)
Greetings. :)

---

### Post by ac5jw on 2013-03-28
I now have a HOSTS file approaching 700 KB in size.  I think I can still fit it onto a floppy disk.

#

# [ Mozilla Firefox Web Browser Support ]

23.49.244.61 mozorg.cdn.mozilla.net
23.49.244.61 support.cdn.mozilla.net
63.245.215.53 developer.mozilla.org
63.245.217.20 mozilla.com [www.mozilla.com](www.mozilla.com)
63.245.217.36 download.mozilla.org
63.245.217.39 download.mozilla.org
63.245.217.50 support.mozilla.org
63.245.217.51 input.mozilla.org
63.245.217.71 affiliates.mozilla.org
63.245.217.86 careers.mozilla.org
63.245.217.86 firefoxflicks.mozilla.org
63.245.217.86 mozillalabs.com [www.mozillalabs.com](www.mozillalabs.com)
63.245.217.99 blog.mozilla.org
63.245.217.105 mozilla.org [www.mozilla.org](www.mozilla.org)
63.245.217.112 addons.mozilla.org
63.245.223.152 webfwd.org [www.webfwd.org](www.webfwd.org)
63.245.223.176 webmaker.org [www.webmaker.org](www.webmaker.org)
66.151.230.193 sendto.mozilla.org
69.58.188.49 mzl.la
72.21.91.19 cdn.mozilla.net
207.97.227.239 github.com [www.github.com](www.github.com)

66.135.59.147 planet.creativecommons.org
66.135.59.147 search.creativecommons.org
66.135.59.147 wiki.creativecommons.org
72.51.46.230 creativecommons.org [www.creativecommons.org](www.creativecommons.org)
204.93.213.40 store.creativecommons.org
204.93.213.41 store.creativecommons.org
204.93.213.42 store.creativecommons.org
204.93.213.44 store.creativecommons.org

#

# [ Linux Ubuntu Operating System ]
# [ Update Manager, Software Center, Automated Downloads, Linux Support ]

66.211.214.131 archlinux.org [www.archlinux.org](www.archlinux.org)
75.126.153.206 cyberciti.biz [www.cyberciti.biz](www.cyberciti.biz)
75.126.153.206 bash.cyberciti.biz
75.126.153.214 nixcraft.com [www.nixcraft.com](www.nixcraft.com)
78.46.78.247 wiki.archlinux.org
85.13.206.219 shop.canonical.com
91.189.88.33 extras.ubuntu.com
91.189.89.88 [www.canonical.com](www.canonical.com)
91.189.89.105 apps.ubuntu.com
91.189.89.106 apps.ubuntu.com
91.189.89.161 webapps.ubuntu.com
91.189.89.220 login.launchpad.net
91.189.89.221 login.launchpad.net
91.189.89.222 launchpad.net
91.189.89.223 launchpad.net
91.189.89.224 answers.launchpad.net
91.189.89.224 [www.launchpad.net](www.launchpad.net)
91.189.89.225 answers.launchpad.net
91.189.89.225 [www.launchpad.net](www.launchpad.net)
91.189.90.40 [www.ubuntu.com](www.ubuntu.com)
91.189.91.13 security.ubuntu.com
91.189.91.13 us.archive.ubuntu.com
91.189.91.14 us.archive.ubuntu.com
91.189.91.15 us.archive.ubuntu.com
91.189.92.150 archive.canonical.com
91.189.92.191 archive.canonical.com
91.189.92.200 archive.ubuntu.com
91.189.92.200 security.ubuntu.com
91.189.92.201 archive.ubuntu.com
91.189.92.202 archive.ubuntu.com
91.189.94.12 ubuntuforums.org [www.ubuntuforums.org](www.ubuntuforums.org)
91.189.94.156 canonical.com
91.189.94.156 ubuntu.com [www.ubuntu.com](www.ubuntu.com)
91.189.94.173 ns1.canonical.com
91.189.95.3 ns2.canonical.com
198.252.206.16 askubuntu.com [www.askubuntu.com](www.askubuntu.com)
207.241.148.80 about.com [www.about.com](www.about.com)
207.241.148.80 linux.about.com
209.6.3.210 ns3.canonical.com

#

---

### Post by ac5jw on 2013-03-28
#

# [ United States Government Official Web Portal ]

12.129.120.24 answers.usa.gov
23.0.249.215 business.usa.gov [www.business.usa.gov](www.business.usa.gov)
23.0.249.215 search.usa.gov
24.25.26.145 [www.firstgov.gov](www.firstgov.gov)
24.25.26.152 [www.firstgov.gov](www.firstgov.gov)
63.150.153.100 business.gov [www.business.gov](www.business.gov)
63.233.110.35 [www.gobiernousa.gov](www.gobiernousa.gov)
63.233.110.43 [www.gobiernousa.gov](www.gobiernousa.gov)
65.121.208.185 m.gobiernousa.gov
65.121.208.202 usa.gov [www.usa.gov](www.usa.gov)
65.121.208.202 [www.seniors.gov](www.seniors.gov)
65.121.208.211 m.gobiernousa.gov
65.121.208.216 usa.gov [www.usa.gov](www.usa.gov)
65.121.208.216 [www.seniors.gov](www.seniors.gov)
65.121.208.232 m.usa.gov
65.121.209.176 m.usa.gov
66.6.36.34 blog.usa.gov
66.6.36.36 blog.usa.gov
159.142.1.220 kids.gov [www.kids.gov](www.kids.gov)
162.140.57.23 [www.welcometousa.gov](www.welcometousa.gov)
162.140.57.90 publications.usa.gov
173.252.148.104 firstgov.gov
173.252.148.104 gobiernousa.gov
173.252.148.104 seniors.gov
184.26.41.215 kids.usa.gov
216.128.241.32 go.usa.gov
216.128.241.47 firstgov.gov
216.128.241.47 gobiernousa.gov
216.128.241.47 seniors.gov
216.128.241.216 my.usa.gov

#

# [ United States Government Services ]

23.62.105.215 [www.howto.gov](www.howto.gov)
63.235.36.17 [www.itdashboard.gov](www.itdashboard.gov)
63.235.36.27 quickfacts.census.gov
63.235.36.67 [www.itdashboard.gov](www.itdashboard.gov)
63.235.37.188 quickfacts.census.gov
66.151.109.33 cfda.gov [www.cfda.gov](www.cfda.gov)
69.25.74.162 change.gov [www.change.gov](www.change.gov)
159.142.4.109 computersforlearning.gov [www.computersforlearning.gov](www.computersforlearning.gov)
159.142.75.50 [www.gsa.gov](www.gsa.gov)
159.142.144.188 gsa.gov
159.142.162.26 gsablogs.gsa.gov
173.252.148.82 apps.gov
173.252.148.83 howto.gov
173.252.148.104 itdashboard.gov
184.72.241.172 federalregister.gov [www.federalregister.gov](www.federalregister.gov)
198.137.240.122 cio.gov [www.cio.gov](www.cio.gov)
204.193.227.133 fedworld.gov [www.fedworld.gov](www.fedworld.gov)
204.193.230.133 ntis.gov [www.ntis.gov](www.ntis.gov)
209.134.55.115 visitthecapitol.gov [www.visitthecapitol.gov](www.visitthecapitol.gov)
216.64.203.235 gsaelibrary.gsa.gov [www.gsaelibrary.gsa.gov](www.gsaelibrary.gsa.gov)
216.64.206.176 gsaelibrary.gsa.gov [www.gsaelibrary.gsa.gov](www.gsaelibrary.gsa.gov)
216.128.241.25 apps.gov [www.apps.gov](www.apps.gov)
216.128.241.25 info.apps.gov [www.info.apps.gov](www.info.apps.gov)
216.128.241.26 howto.gov
216.128.241.47 itdashboard.gov

166.78.88.32 support.govdelivery.com
208.42.190.14 service.govdelivery.com
208.42.190.21 links.govdelivery.com
208.42.190.23 admin.govdelivery.com
208.42.190.24 public.govdelivery.com
209.167.231.15 direct.govdelivery.com
216.243.167.169 govdelivery.com [www.govdelivery.com](www.govdelivery.com)

#

---

### Post by ac5jw on 2013-03-28
#

# [ United States Postal Service, US Mail ]

23.0.248.70 about.usps.com
23.0.248.70 tools.usps.com
23.0.248.70 [www.usps.com](www.usps.com)
23.0.248.70 [www.usps.gov](www.usps.gov)
23.62.104.70 cns.usps.com
56.0.34.75 gateway.usps.com
56.0.34.79 reg.usps.com
56.0.34.122 moversguide.usps.com
56.0.34.133 faq.usps.com
56.0.134.100 usps.com
56.0.156.39 ehome.uspis.gov
56.0.156.41 postalinspectors.uspis.gov
56.0.156.41 uspis.gov [www.uspis.gov](www.uspis.gov)
56.0.195.105 ribbs.usps.gov
65.242.3.5 uspsoig.gov [www.uspsoig.gov](www.uspsoig.gov)
65.254.60.26 uspsvideo.com [www.uspsvideo.com](www.uspsvideo.com)
69.25.225.93 stamps.com [www.stamps.com](www.stamps.com)
184.26.40.70 shop.usps.com
184.26.40.70 store.usps.com

#

---

### Post by ac5jw on 2013-03-28
#

# [ White House ]

23.1.44.110 apply.whitehouse.gov
23.1.44.110 petitions.whitehouse.gov
63.233.110.8 [www.wh.gov](www.wh.gov)
63.233.110.42 [www.wh.gov](www.wh.gov)
165.254.44.115 [www.whitehouse.gov](www.whitehouse.gov)
165.254.44.171 [www.whitehouse.gov](www.whitehouse.gov)
184.26.156.110 whitehouse.gov
198.246.60.122 whitehousegiftshop.com [www.whitehousegiftshop.com](www.whitehousegiftshop.com)
204.245.162.17 wh.gov
204.245.162.49 wh.gov
209.251.178.107 whitehousehistory.org [www.whitehousehistory.org](www.whitehousehistory.org)

#

---

### Post by stinkeye on 2013-03-28
Why don't you just attach your hosts file?

---

### Post by ac5jw on 2013-03-28
I can attach a HOSTS file?  I will try to figure out how to do that

---

### Post by stinkeye on 2013-03-28
> **ac5jw said:**
> I can attach a HOSTS file?  I will try to figure out how to do that
Copy it to your home folder ....Right click on the file > **compress** as tar.gz and use the paper clip icon to attach.
I'm not sure what the hosts file contains, so make sure there is no revealing info in it.

---

### Post by ac5jw on 2013-03-28
OK, I think I figured out how to give an attachment.  But, my HOSTS file is too large for this forum to accept it in one segment.  I would have to break it down anyway to stay under 19.5 KB.

R

---

### Post by ac5jw on 2013-03-28
ok I will try to follow your suggestion now.  Thanks !

R

---

### Post by ac5jw on 2013-03-28
OK I compressed it to the tar.gz as you instructed, but I am concerned about the file size at 22.5 KB.  I am not sure if the forum will accept it but I will try to find out now.

R

---

### Post by ac5jw on 2013-03-28
[ATTACH]240665[/ATTACH]

---

### Post by ac5jw on 2013-03-28
Thanks for explaining how to attach the file.  I never did it before, and it appears to have worked the first time !

R

---

### Post by stinkeye on 2013-03-28
Yep ,downloads ok.
Limit for an archive is 976.6 KB.
You don't have to actually insert the attachment in the post.
You can if you want but if you don't, any attachments will be shown in a box 
at the bottom of your post.

```
You can also use the code icon (#) by highlighting a section of text then 
hitting the # icon to put it in a code box as I have done here.
```

---

### Post by ac5jw on 2013-03-28
I also have a footer.txt file that I concatenate with the header.txt to create the HOSTS file.  But it is just a lot of 127.0.0.1 entries for unwanted domains and hosts.  I did not see much point in sharing that portion.

R

---

### Post by ac5jw on 2013-03-28
Thanks for your help with my navigation in the Thread.  It is a big help and I am learning a lot.

R

---

### Post by pfeiffep on 2013-03-29
I'm positive this speeds up internet access to those sites that you've entered! However the Domain Name Service is a pretty powerful tool - within a few hours an IP address change is propagated to core routers on the internet. Just the time you actually need access to one of the sites your manually entered you might have to resolve the name outside. I certainly would NOT suggest that you use this method for automating anything outside your own network

---

### Post by CharlesA on 2013-03-29
> **pfeiffep said:**
> I'm positive this speeds up internet access to those sites that you've entered! However the Domain Name Service is a pretty powerful tool - within a few hours an IP address change is propagated to core routers on the internet. Just the time you actually need access to one of the sites your manually entered you might have to resolve the name outside. I certainly would NOT suggest that you use this method for automating anything outside your own network

Pretty much this. The only thing I would use the hosts file for is testing the configuration of a web server/email server.

The only real difference adding a ton of entries to your hosts file does is cut down on the amount of time it takes to query a DNS server and return a result. The time it takes to do that is usually only a few milliseconds.

---

### Post by ac5jw on 2013-03-29
OK, thanks for the advice.  All I know is that my computer started displaying the web a lot faster after I added the HOSTS file entries.  Even the display was slow after I switched DNS servers.  I will keep watch on my web service and if it gets problematic I will get new nslookup data on any slow websites.

R

---

### Post by vasa1 on 2013-03-29
> **ac5jw said:**
> Hey, I had a problem over the past three years with my computer taking forever to **resolve URLs**.  ... I began to study about creating a HOSTS file from scratch as a means to do domain and host name blocking for uninvited advertisements.
...
Just a clarification: does OP mean "loading pages" instead of "resolving urls"? (I get how blocking content will display a page faster.)

---

### Post by ac5jw on 2013-03-29
I really don't know the difference at this point.  All I know is it took long waits for handoffs, linking, and display of web pages I visited.  But after creating HOSTS entries to support the places I visit, it really turned around and displayed content a lot faster.  Does that help ?  And I have a lot of blocked domains and hosts, but that never affected my slow download time.  My downloads and displays of content went a lot faster only after I began to use the HOSTS entries.


R

---

### Post by ac5jw on 2013-03-29
Before I created my first HOSTS file, I was using the mintNanny domain blocker.  I had slower access to the web even then, so I cannot conclude that the domain blocking helped to speed up the permitted data.

R

---

### Post by deadfish00 on 2013-03-29
Great job on your Host files. It might also help if you want to block is to install adblocker plugins for your browser. It's pretty effective on chrome and firefox.

---

### Post by ac5jw on 2013-03-29
Thanks for the advice on plugins.  I tend to use my footer section for blocking domains and I am happy with that solution.  I will try to install a new update which is expanded for more government and video sites.

R

---

### Post by ac5jw on 2013-03-29
Here is my latest complete HOSTS file which I name NewHOSTS.txt until I am finally moving it into the hosts file directory.  I learned to copy NewHOSTS.txt into my /etc/hosts.txt as a ready backup and it is easier to sudo cp /etc/hosts.txt /etc/hosts :)[ATTACH]240720[/ATTACH]

---

### Post by mharv on 2013-03-30
This does NOTHING to speed up anything. The only possibility this has is for an inexperienced user to screw something up and negatively impact their ability to access the internet. Please don't come on here encouraging people to do stupid stuff when you clearly have little understanding of what you're doing. Do you really think in the past 20+ years not one other person has known about the host file is or what DNS is and that you just discovered some secret? No, you just discovered the outdated PRE-DNS way of doing things.

Like the previous post, use this for naming LOCAL hosts. Use a firewall for filtering outside hosts. And if DNS resolving is a problem then change your DNS servers.

---

### Post by ac5jw on 2013-03-31
Thanks for your comment.  I am studying networking with Linux and learned alot in the past few weeks by creating a hosts file.  It has so far been very helpful to my work online and I noticed a vast improvement in connection speed.  I have also been maintaining my Ubuntu software updates as well, so the hosts file is not the only thing changing on my system.

For the results I am getting, I will continue to use my hosts file as a tool to keep connections running smoothly.  I am also studying about other ways to maintain rapid access online, and as you suggest, that includes DNS options.  I did change my DNS servers once and after a few hours I noticed a shorter time for web browser displays.  At that time, I had not yet implemented a hosts file but it was close to the time I was creating my original test hosts file.

Because I have been using this hosts file for a few weeks, I have encountered host and domain changes as well as dropped IP addresses.  So far, I have kept up with the updates.  I am operating on the philosophy that IPv4 addresses are less likely to change now because they are harder to obtain.  So I think most domains will continue to use their IPs and keep them stable.  I am therefore not too worried about updating my hosts file as necessary.

I experienced a drop in time for connections that I can only point to a change in DNS and a change in my hosts file, which used to be empty except for the entries stamped in by Ubuntu OS installation.  So I think I am pretty close to the source of whatever it is that is keeping my Internet going.

R

---

### Post by mharv on 2013-04-01
I was also studying Linux networking at when I found out about the hosts file and tried the exact same thing you did. Use Wireshark or tcpdump to record your traffic for a little while and then write a script to calculate the percentage of bits of your traffic that DNS requests make up.

---

### Post by jonobr on 2013-04-01
INteresting thread.


Just a bit of history though.... Well this is the way I was taught!!

The host file was used to do name resolution. 
It  would be created and maintained by a central authority and it would be distributed to the community.
The host files became inconsistent, large, out of date quickly and just unworkable.

That lead to the idea of DNS and its associated hierarchy to get away from those bulky hosts files that ended up causing misery.

Again, that's what I was told when I was learning networking, I am open to correction, but this is the reverse Neal Armstrong moment:-)

Peace!

---

### Post by CharlesA on 2013-04-01
That is pretty much the history of the hosts file. It starts back in sneakernet when resources were statically assigned. Now it's easier to just use DNS to do name resolution because of the sheer amount of hosts on the Internet and how quickly things can change.

---

### Post by wbar2 on 2013-04-08
There is a site that maintains a large hosts file that blocks ad / spam / malware content:
[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

Additionally here is a method to update it automatically:
[http://www.putorius.net/2012/01/block-unwanted-advertisements-on.html](http://www.putorius.net/2012/01/block-unwanted-advertisements-on.html)

This is not for normal DNS resolution to get to your favorite site (although you can append it to it as previously stated). This site has a file just for blocking unwanted sites.

---

