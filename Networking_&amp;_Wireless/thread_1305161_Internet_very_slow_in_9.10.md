---
title: "Internet very slow in 9.10?"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by safcrob2008 on 2009-10-29
This is probably the 1000th time this has been asked, any reason, any fixes?

Running wireless off 25MB cable broadband, was fine in 9.04

---

### Post by ljrmorgan on 2009-10-29
Can you be more specific??

I know a lot of people (inc. me) were having problems with DNS - web pages take ages to load and the status bar says "resolving host".

---

### Post by caulkins on 2009-10-29
> **ljrmorgan said:**
> I know a lot of people (inc. me) were having problems with DNS - web pages take ages to load and the status bar says "resolving host".

Yes, that's the trouble I'm having, only the status bar says "Looking up [website]..."  What is the fix?  When I've had this trouble in the past, it was because my Actiontec DSL gateway puts an incorrect DNS address in the first spot.  The solution was to manually edit /etc/resolv.conf and then do "sudo chattr +i resolv.conf" to keep it from being rewritten.  Unfortunately, that isn't working for me now.

---

### Post by voodoo_child on 2009-10-29
I had the same issue and fixed it by putting in my DNS servers manually. 

Click on your network settings, then go into the ivp4 settings and change it to Automatic (DHCP) Adresses only. Then put in your two DNS servers in the DNS box (separated by a comma). 

Reboot. 

Worked for me, worth a shot.

---

### Post by caulkins on 2009-10-30
> **voodoo_child said:**
> Click on your network settings, then go into the ivp4 settings and change it to Automatic (DHCP) Adresses only. Then put in your two DNS servers in the DNS box (separated by a comma). 

Reboot. 


That did the trick for me as well; thank you!

---

### Post by AEDan1977 on 2009-10-30
I was having the same problem with my Dell Studio XPS 1640 w/ Intel WiFi 5300.   I noticed on the 5GHz wireless network the webpages would not load, internet was slow, the dns server fix kind of worked.  I switched to the 2.4GHz network and it worked fine... dunno if anyone else has this same issue.  5GHz works fine when I switch over to Windows 7.

- Dan

---

### Post by axelsvag on 2009-10-30
I have the same problem as you after upgrade to karmic. I feel really stupid but which dns numbers am I suppose to put in?

---

### Post by atarax42 on 2009-10-30
you can try one or two of these:
[http://www.opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns](http://www.opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns)

---

### Post by axelsvag on 2009-10-30
I feel even more stupid. Why should I use a dns server that is not connected to my isp. Or have I misunderstood your problems. Everything worke perfectly with 9.04 after the upgrade to 9.10 the connection went up 10-15 % but connection to several sites is extremely slow. But if I test the speed to a speed test site I got extremeley good speed.

---

### Post by atarax42 on 2009-10-30
i'm not an expert, but i guess the dns-server is independent from the provider even if the isp generally has its own dns-server. but obviously you can choose your own dns-server. the connection speed indicates the time the data you requested from a web-server is transmitted to you, but name resolving via the dns is a separate process that is performed first. this explains why with karmic a page request is delayed for a few seconds until the name resolving is complete and after this downloads are performed at normal speed.

would be great if someone could analyse why this bug is new with karmic and would file a decent bug-report...

---

### Post by axelsvag on 2009-10-30
Maybe I am doing something, but I put one of the dns adresses in the link above in Network Manager edit settings, under the ipv4 menu. 
At the bottom there is a box called " DHCP-client ID " I put the dns DNS adress there is that totally wrong since I do not notice any improvement?

---

### Post by atarax42 on 2009-10-30
you have to select the method "automatic (DHCP) **addresses only**" first, then you put the dns ips comma separated into the form field "dns-server". that's what i did. confirm this dialogue and reboot.

---

### Post by axelsvag on 2009-10-30
I must be in the wrong setting dialogue since I do not find any of the text you are refering to. So it is not in the network manager settings you do this change?

---

### Post by atarax42 on 2009-10-30
maybe the text strings are a bit different, because i use the german localisation. go to system > settings > network connections. select the connection you use and click on "edit". then follow the procedure as mentioned.

you can also start the app in the terminal: nm-connection-editor

---

### Post by axelsvag on 2009-10-30
It seems to be the same as I find. But when I go to the ipv4 menu I got a row at the top thats says " Method  Automatic (DHCP) " and at the bottom I just find a row called " DHCP-Client-ID " am I on the right track?

---

### Post by atarax42 on 2009-10-30
yes you are. the row at the top thats says "Method Automatic (DHCP)" is a drop-down list where you have to select "Automatic (DHCP) **addresses only**". not before you have done so you can access the form field to enter the dns-server ip. good luck!

---

### Post by axelsvag on 2009-10-30
Thank you I found it now. I feel so stupid. Now I will try some of the dns adresses recomended in the link

---

### Post by atarax42 on 2009-10-30
how can you feel stupid now that you have learned something?

---

### Post by Jannes. on 2009-10-30
this helped for me 

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

---

### Post by atarax42 on 2009-10-30
great. i hope you are aware that there are some privacy issues with opendns:
[http://en.wikipedia.org/wiki/OpenDNS#Privacy_issues.2C_conflicts_and_covert_redirection](http://en.wikipedia.org/wiki/OpenDNS#Privacy_issues.2C_conflicts_and_covert_redirection)

---

### Post by Jannes. on 2009-10-30
did not know that...

So i'll delete it?! grtz

---

### Post by atarax42 on 2009-10-30
as you like. i'd rather use ips from here:
[http://www.opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns](http://www.opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns)

---

### Post by axelsvag on 2009-10-31
Thank you every one it really helped the speed. But my last question is what happened with karmic 9.10 since the speed is perfect on jaunty and the dists before?

---

### Post by megahurts on 2009-10-31
Manually setting the DNS servers sorted it out for me too.  Luckily I know my ISPs DNS servers off the top of my head after having a few issues with my router.  For those of you that don't you should be able to determine them using your router's web management pages (at least you can on my old Linksys one and the el-cheapo Belkin one I'm currently using).  It's usually displayed in the System Status pages.  You can also find out using a windows box by starting a command propmt and typing ipconfig /all

---

### Post by iamgeniusrnti on 2009-10-31
Let me start off by saying, I am completely new to Linux and this community.  I read Linux material for about a month and did a Wubi install about a week and a half ago. Now, I'm searching for a netbook so I  can do a full install.

I think it can be established beyond shadow of all doubt there's a bug with 9.10.  What's really odd, is when I look at other treads and forums, there's nay-sayers; folks saying "nah... it's perfectly normal and I like to get a cup of coffee while we resolve the host name" LMAO!!!!

My question is, when a new distro comes out and a bug is discovered, how long does it take before a patch is produced solving the issue?

I grabbed the two DNS addresses from my router's GUI and manually added the DNS servers for my ISP.  I then went into firefox and did the about:config edit and that made the problem go away.  But not really sure that blocking and hiding from ipv6 is truly the solution but more of a bandaid... agree/disagree?

---

### Post by axelsvag on 2009-10-31
I have used diferent flavours of Ubuntu for three years and you see I still ask newbie questions. My experience is that there is seldom a bug that give a real problem. So my impression is that this karmic koala 9.10 is unique to have a lot of bugs remaining after the release. But you can get an older wubi based on 9.04 if you want a more stable version. But then you will miss the nice new features.

---

### Post by iamgeniusrnti on 2009-10-31
> **axelsvag said:**
> I have used diferent flavours of Ubuntu for three years and you see I still ask newbie questions. My experience is that there is seldom a bug that give a real problem. So my impression is that this karmic koala 9.10 is unique to have a lot of bugs remaining after the release. But you can get an older wubi based on 9.04 if you want a more stable version. But then you will miss the nice new features.

LMAO!  Are you kidding?  I upgraded my wubi 9.04 to 9.10 just so I can see what all the fuss is about--gotta admit I kind of like the new look. Windows only ever does this once every couple years, looks like Ubuntu gets a new face atleast once a year?

Nah, I'll wait for the fixes.

---

### Post by axelsvag on 2009-10-31
Actually every 6 months (9.04 2009 april), (9.10 2009 october), (10.04 2010 april) etc.

---

### Post by LeChuck on 2009-10-31
> **Jannes. said:**
> this helped for me 

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

I am excited ... that fixed the problem for me too!

Anyway, it has to be **Wireless** and _not_ **Wired** as shown in the instruction.

Cheers

---

### Post by adm1968 on 2009-10-31
> **voodoo_child said:**
> I had the same issue and fixed it by putting in my DNS servers manually. 

Click on your network settings, then go into the ivp4 settings and change it to Automatic (DHCP) Adresses only. Then put in your two DNS servers in the DNS box (separated by a comma). 

Reboot. 

Worked for me, worth a shot.
[FONT="Georgia"]Thanks!
Same problem here. I did exactly what you said, and everything is working now :D

Should this be explained? (bug/no bug)[/FONT]

---

### Post by HammerHed on 2009-11-10
This fixed the problem for me: [http://www.craigmayhew.com/blog/2009/11/slow-dns-lookups-in-firefox-on-ubuntu-9-10-karmic-koala/]("http://www.craigmayhew.com/blog/2009/11/slow-dns-lookups-in-firefox-on-ubuntu-9-10-karmic-koala/")

The workaround in firefox is to go to “about:config”, just type it into the address bar and hit enter. Then change the value network.dns.disableIPv6 to TRUE.

---

### Post by HammerHed on 2009-11-10
Actually this only fixed the issue in FireFox, this bug affects all web apps.

There is a much larger issue here than just FireFox

See bug @ LaunchPad: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757")

---

### Post by jt_04 on 2009-11-10
> **voodoo_child said:**
> I had the same issue and fixed it by putting in my DNS servers manually. 

Click on your network settings, then go into the ivp4 settings and change it to Automatic (DHCP) Adresses only. Then put in your two DNS servers in the DNS box (separated by a comma). 

Reboot. 

Worked for me, worth a shot.

this worked for me, in combination with disabling ipv6 in firefox.  I used the DNS servers listed in my router's status page.  i didn't even need to reboot, just disable/enable networking.  many thanks.  :D

---

### Post by iamgeniusrnti on 2009-11-10
> **jt_04 said:**
> this worked for me, in combination with disabling ipv6 in firefox.  I used the DNS servers listed in my router's status page.  i didn't even need to reboot, just disable/enable networking.  many thanks.  :D

Yea, but that really doesn't solve the issue it just band aids it.  If you force the DNS to your ISP and then go to Starbucks and DHCP in, you are back at square one unless you use OpenDNS.

Hopefully the Linux Gods will figure it out LOL!

---

### Post by jt_04 on 2009-11-11
> **iamgeniusrnti said:**
> Yea, but that really doesn't solve the issue it just band aids it.  If you force the DNS to your ISP and then go to Starbucks and DHCP in, you are back at square one unless you use OpenDNS.

Hopefully the Linux Gods will figure it out LOL!

true, but i won't be taking my htpc to starbucks any time soon.  i've learned my lesson though, don't rush to upgrade ubuntu if everything is working fine already.

---

### Post by beachez on 2009-11-11
This worked for me!  I changed my wireless settings to 
"Click on your network settings, then go into the ivp4 settings and change it to Automatic (DHCP) Adresses only. Then put in your two DNS servers in the DNS box (separated by a comma)."  I used two address off the [Opennic]("http://opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns") site and then disabled/enabled wireless networking, no restart needed.  Can anyone confirm that these dns servers should work from any normal location?  Thanks to all for the suggestions! Fixed my last annoying issue with Karmic![URL="http://opennicproject.org/index.php/start-here/51-migrate-to-opennic/75-public-dns"]
[/URL]

---

