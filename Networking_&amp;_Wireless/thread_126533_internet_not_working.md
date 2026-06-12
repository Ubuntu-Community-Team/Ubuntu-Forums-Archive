---
title: "internet not working"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by bountonw on 2006-02-06
I thought I posted a thread on this last night, but after searching my user name can't find it.  I must have done something wrong.

Anyway, I am a new user and successfully installed ubuntu (single boot) on my office computer (I'm the boss.)  I also installed dual boot at home (with Windows XP).  The office installation automatically recognized my DSL internet connection, but my home computer when booting in Ubuntu doesn't.

As I can't use internet yet, i will need to re-boot between windows/linux to study/experiment.

---

### Post by bountonw on 2006-02-06
Well I finally found my other post, but no one replied to that one either.  I had done the thread in the absolute beginner forum.  I am not sure where this question should be dealt with. I should only have one thread open on the same subject, but am not sure which one to delete.  If the modorator wants to delete one of my threads on this, that is fine.  I am sorry to double post.  I had thought that I had some how lost my other thread on this.

Anyway, back to the question at hand.  I would like to use the internet on ubuntu here at home.  Can anyone help me?

---

### Post by bountonw on 2006-02-06
Live and learn.  I have been searching around and have found the following sites.  Printed over 50 pages and am going to try to solve the problem.  If anyone else has this problem.  I recommend the following links.

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
[http://ubuntuforums.org/showthread.php?t=125185](http://ubuntuforums.org/showthread.php?t=125185)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)

I printed all of these so should be well armed and dangerous.  Will log back in and post if it works for others who may have the same problem.

---

### Post by Jedeye on 2006-02-06
good luck... let us know about your results.

---

### Post by bountonw on 2006-02-06
I got firefox to work by disabling ipv6 in about:config as explained step by step in 

[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)


I can not get gaim to work, however and tried 

```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

as suggested in [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

no change in Gaim after re-booting.  Not sure what to do next as far as gaim is concerned.

---

### Post by bountonw on 2006-02-08
I solved my internet connection problem and have updated and upgraded successfully. The following link was the ticket for me. I read through the entire thread trying things until I found the answer in post #28. Not sure what it all means, but glad that it worked.

[http://www.ubuntuforums.org/showpost...1&postcount=28](http://www.ubuntuforums.org/showpost...1&postcount=28)

I wish I knew how to edit [RESOLVED] in the original post.

---

### Post by mips on 2006-02-08
[QUOTE=bountonw]I solved my internet connection problem and have updated and upgraded successfully. The following link was the ticket for me. I read through the entire thread trying things until I found the answer in post #28. Not sure what it all means, but glad that it worked.

[http://www.ubuntuforums.org/showpost...1&postcount=28](http://www.ubuntuforums.org/showpost...1&postcount=28)

I wish I knew how to edit [RESOLVED] in the original post.[/QUOTE]

That link/URL does not work ???

---

### Post by bountonw on 2006-02-08
Sorry, I didn't double check the link.  I was trying to link to the post instead of the page.  I would still like to be able to link to posts and goto posts directly.  I think that it would be easier than going to the page all the time.

[http://www.ubuntuforums.org/showthread.php?t=125185&page=3](http://www.ubuntuforums.org/showthread.php?t=125185&page=3)
post #28 is the relevent post.

The funny thing is that when I woke up this morning I couldn't log into gain again and checked the /etc/resolv.conf file and it had for some reason reverted back to the original settings.  I changed it and re-set it and am connected happily.  Can you explain what is going on?  

Thank you mips for providing the answer in the above mentioned thread that lead to me getting connected again.  Now to only understand what I did and to know how to make the changed perminent.

---

### Post by bountonw on 2006-02-09
Back on my home computer.  Why aren't the changes I make per


[http://www.ubuntuforums.org/showthread.php?t=125185&page=3](http://www.ubuntuforums.org/showthread.php?t=125185&page=3)
post #28 is the relevent post.


permenant?  Everytime I boot up, I have to sudo gedit...

Is there a way of making this change permenant?

---

### Post by mips on 2006-02-09
I assume you are using DHCP ? If this is the case then the information provided to your pc via DHCP is overwriting your network config.

1. You could try and log into your router and manually adding the DHCP server info in the routers config and hopefully it will pass this on to the PC.

2. From Option3 look at this link [http://www.ubuntuforums.org/showthread.php?t=11544](http://www.ubuntuforums.org/showthread.php?t=11544)  post#2

---

### Post by bountonw on 2006-02-09
Thank you mips.  Yes I am using DHCP.  I found that out by clicking on System > Administration > Networking >Ethernet Connection >Properties.

[COLOR="Red"]How would I find this out using command line?[/COLOR]

Regarding your option 1, I have absolutely no idear of how to log onto my router manually.

I have commented out the following line of  /etc/resolv.conf
nameserver 192.168.1.1 

[To comment out a line put the '#' sign at the beginning of the line.]

For all of you experienced people that have been helping me along, I appreciate it.  The reason I trying to document each step and add explanations is in the hope that there are others like me that are completely clueless at times.  Very steep learning curve here for us mortals.

---

### Post by mips on 2006-02-09
[QUOTE=bountonw]Thank you mips.  Yes I am using DHCP.  I found that out by clicking on System > Administration > Networking >Ethernet Connection >Properties.

[COLOR="Red"]How would I find this out using command line?[/COLOR][/QUOTE]

cat /etc/network/interfaces

You should see a line that reads:
```
iface eth0 inet dhcp
```

Alternatively if it was static it would have the word 'static' instead of dhcp followed by the full tcp/ip config.

I cant think of an easier way to do this now.

[QUOTE=bountonw]
Regarding your option 1, I have absolutely no idear of how to log onto my router manually.[/QUOTE]

Open a web browser and point it to your routers IP Address. You will be presented with a WebAdmin interface to your router. Probably requires username&password but those are easy to find. From there onwards everything is point&click.

[QUOTE=bountonw]
I have commented out the following line of  /etc/resolv.conf
nameserver 192.168.1.1 

[To comment out a line put the '#' sign at the beginning of the line.]

For all of you experienced people that have been helping me along, I appreciate it.  The reason I trying to document each step and add explanations is in the hope that there are others like me that are completely clueless at times.  Very steep learning curve here for us mortals.[/QUOTE]

Did that work ?

---

### Post by bountonw on 2006-02-09
Commenting out
#nameserver 192.168.1.1

didn't work for some reason.

This morning I noticed that my /etc/resolv.conf is back to default and I have a new file /etc/resolv.conf~ that has 

nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1

I can't understand why the last line isn't commented out on this.  Also can't understand why the file name change *conf~

I am glad I know how to manually solve the problem every time I reboot, but it would be nice to not have to worry about it.  I also don't understand the numbers in the 3 lines.  They must be what are calle IP addresses???  What do they go to???

---

### Post by mips on 2006-02-09
[QUOTE=mips]I assume you are using DHCP ? If this is the case then the information provided to your pc via DHCP is overwriting your network config.

1. You could try and log into your router and manually adding the DHCP server info in the routers config and hopefully it will pass this on to the PC.

2. From Option3 look at this link [http://www.ubuntuforums.org/showthread.php?t=11544](http://www.ubuntuforums.org/showthread.php?t=11544)  post#2[/QUOTE]


Please try one of the above two suggestions as i'm sure they will solve your problem.

---

### Post by mips on 2006-02-09
[QUOTE=bountonw]Commenting out
#nameserver 192.168.1.1

didn't work for some reason.

This morning I noticed that my /etc/resolv.conf is back to default and I have a new file /etc/resolv.conf~ that has 

nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1

I can't understand why the last line isn't commented out on this.  Also can't understand why the file name change *conf~

I am glad I know how to manually solve the problem every time I reboot, but it would be nice to not have to worry about it.  I also don't understand the numbers in the 3 lines.  They must be what are calle IP addresses???  What do they go to???[/QUOTE]


Because everythime you reboot the config file is overwritten by the dhcp parameters.

*conf~ is usually a temporary file or a backup.

The numbers in the three lines are IP Addresses. They refer specifically to the IP addresses of 2 Internet DNS/Name servers and your router which is trying to act as a dns/name server. When you type "www.google.com" into your browser your pc has zero clue as to what that actually means and it is even less understandable by tcp/ip. So what happens. Your PC communicates with the DNS server and says, "Hey whats the IP address for www.google.com". The DNS server responds with a IP address for the google server. Your PC now uses that IP address given to it by the DNS server to communicated withthe google server. The [www.google.com](www.google.com) thing is just for us humans that cant remember numbers so well and work better with names.

---

### Post by bountonw on 2006-02-09
Thank you mips for your continued patience.

I did the option2 that you mentioned. changing the DNS Server in Networking by deleting  192.168.1.1

and adding
 61.1.96.69
 61.1.96.71
 When I reboot, I still have the same problem.  Everything reverted back.  I will try loggin on to my router as you say.  

(Got the ADSL Modem screen, but the password that I have written down doesn't work.  Will call my service provider.)

---

### Post by mips on 2006-02-10
Did you do everything in post#2 from the above link ???

[COLOR="Red"]Finally, go to **/etc/dhcp3/dhclient-script** and comment out this:[/COLOR]

```
# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}

```

---

### Post by bountonw on 2006-02-10
IT WORKED:-D Thank you for your patience mips.  Victory!!!

Now, how do I edit my original post to say (RESOLVED).  I know that it is right in front of my nose, but I still haven't figured it out.

---

### Post by mips on 2006-02-10
Click on edit and next to the save button click on advanced, somewhere in there. You can rate the post and also change the subject.

---

