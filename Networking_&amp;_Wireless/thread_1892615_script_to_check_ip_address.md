---
title: "script to check ip address"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2011-12-08
I have a home network which I have SSH set up on.  I would like to be able to dial my home network remotely but my ip address changes at least once a day.  I called my ISP to see if they can provide me with a static IP address, but they charge a lot of money to lease static IPs to compensate for the assumed increase in bandwidth of running a server.
I don't plan on running a game server or anything that requires a lot of bandwidth so I don't want to spend the extra money.
So my plan was to create a simple script that would query my external IP address, echo it to a file and then email the contents of that file to myself at regular intervals.
I've gotten the first part of the script working and it does echo my external IP.  However, the second part which would then email the script to myself I can't figure out.  Then the third part I guess would be to run a cron job that will execute the script.

Here is my script so far.

```


#!/bin/bash

IPFILE=/home/user/ipaddress

CURRENT_IP=$(wget http://www.whatismyip.org -O - -o /dev/null)

MAIL_FROM="From: insert@email.address-here"

if [ -f $IPFILE ]; then
KNOWN_IP=$(cat $IPFILE)
else
KNOWN_IP=
fi

if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
echo $CURRENT_IP > $IPFILE

MAIL_SUBJECT="IP address at home"
MAIL_BODY="The IP address at home has been changed to $CURRENT_IP. Update SSH client now."

echo $MAIL_BODY | mail -a "$MAIL_FROM" -s "$MAIL_SUBJECT" -c insert@email.address-here
logger -t ipcheck -- IP changed to $CURRENT_IP
else
logger -t ipcheck -- No IP change
fi

```

When I execute the script, my IP address is echoed to ~/ipaddress.  But mail is not being sent to my email address.  Do I need to configure mail?  I installed 'mailutils' and set the server settings to 'internet site' since I use gmail.  Is that incorrect?

---

### Post by dmizer on 2011-12-08
This is a much better solution rather than emailing your IP:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

In short:
Configure your router to automatically update your free dynamic domain name URL, or use ddclient on your ssh server to do it.

Then you can ssh to: [noparse]ssh you@yourdnsdomain.com[/noparse] instead of having to type in a new IP address every time.

---

### Post by N00b-un-2 on 2011-12-08
that was going to be plan B actually.  Mostly I was trying to see if I could get the script to work :lolflag:

---

### Post by dmizer on 2011-12-08
> **N00b-un-2 said:**
> that was going to be plan B actually.  Mostly I was trying to see if I could get the script to work :lolflag:

To get the script to work, you would indeed have to configure sendmail on your server. In most cases, ISPs have smtp blocked (anti spam) so you'd have to jump through some pretty difficult hoops to get everything working. Not impossible though.

---

### Post by N00b-un-2 on 2011-12-08
I registered at freedns.afraid.org.  I was able to ssh to my home computer from my phone using my name server/dns/whatever you call it.  However, I have my doubts that when my ip changes it's going to continue working.

---

### Post by dmizer on 2011-12-08
> **N00b-un-2 said:**
> I registered at freedns.afraid.org.  I was able to ssh to my home computer from my phone using my name server/dns/whatever you call it.  However, I have my doubts that when my ip changes it's going to continue working.

That's why you need to install and configure ddclient: [https://help.ubuntu.com/community/DynamicDNS#Using_a_software_utility_to_perform_Dynamic_DNS_Updates](https://help.ubuntu.com/community/DynamicDNS#Using_a_software_utility_to_perform_Dynamic_DNS_Updates) :)

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> I have a home network which I have SSH set up on.  I would like to be able to dial my home network remotely but my ip address changes at least once a day.  I called my ISP to see if they can provide me with a static IP address, but they charge a lot of money to lease static IPs to compensate for the assumed increase in bandwidth of running a server.
I don't plan on running a game server or anything that requires a lot of bandwidth so I don't want to spend the extra money.
So my plan was to create a simple script that would query my external IP address, echo it to a file and then email the contents of that file to myself at regular intervals.
I've gotten the first part of the script working and it does echo my external IP.  However, the second part which would then email the script to myself I can't figure out.  Then the third part I guess would be to run a cron job that will execute the script.

Here is my script so far.

```


#!/bin/bash

IPFILE=/home/user/ipaddress

CURRENT_IP=$(wget http://www.whatismyip.org -O - -o /dev/null)

MAIL_FROM="From: insert@email.address-here"

if [ -f $IPFILE ]; then
KNOWN_IP=$(cat $IPFILE)
else
KNOWN_IP=
fi

if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
echo $CURRENT_IP > $IPFILE

MAIL_SUBJECT="IP address at home"
MAIL_BODY="The IP address at home has been changed to $CURRENT_IP. Update SSH client now."

echo $MAIL_BODY | mail -a "$MAIL_FROM" -s "$MAIL_SUBJECT" -c insert@email.address-here
logger -t ipcheck -- IP changed to $CURRENT_IP
else
logger -t ipcheck -- No IP change
fi

```When I execute the script, my IP address is echoed to ~/ipaddress.  But mail is not being sent to my email address.  Do I need to configure mail?  I installed 'mailutils' and set the server settings to 'internet site' since I use gmail.  Is that incorrect?


If you intend to do an email script, here is a very simple one.

You need curl and mailutils

sudo apt-get install curl
sudo apt-get install mailutils
> 
#!/bin/bash
 echo "Current IP is $(curl www.whatismyip.org)" | mail -s "IP Address" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]

put it into your crontab to run once a day or however often you need

---

### Post by collisionystm on 2011-12-08
Here I wrote a better one.
This will do its own automatic check for an IP change. If the ip changes it will notify you via email.

> #!/bin/bash
echo $(curl [www.whatismyip.org](www.whatismyip.org)) > ~/ipaddress.txt
if [ "x$(curl www.whatismyip.org)" = "x$(cat ~/ipaddress.txt)" ]
then
exit    
else
        echo "Current IP is $(curl www.whatismyip.org)" | mail -s "Your IP Address has changed" mail@domain
fi



Run that in a crontab

---

### Post by N00b-un-2 on 2011-12-08
the problem i'm running into is that when I run mail no email is sent.  I installed mailutils, but I don't think I have it configured right.

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> the problem i'm running into is that when I run mail no email is sent.  I installed mailutils, but I don't think I have it configured right.

There is nothin to configure in mail utils

---

### Post by N00b-un-2 on 2011-12-08
do I need to configure an smtp server like exim4?  I am not really sure how sending mail from your system works.

---

### Post by Lars Noodén on 2011-12-08
> **collisionystm said:**
> Here I wrote a better one.
This will do its own automatic check for an IP change. If the ip changes it will notify you via email.
Run that in a crontab

The write to the file has to occur after the test if the number has changed.  Otherwise it will never be identified as changed.  Also, [wget](http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html) is part of the basic distro.

```

#!/bin/bash
IPADDRESS=$(wget -O - www.whatismyip.org 2>/dev/null)
if [ "x${IPADDRESS}" = "x$(cat ~/ipaddress.txt)" ]
then
 exit
else
 echo "Current IP is ${IPADDRESS}" | mail -s "Your IP Address has changed" mail@domain
fi
echo ${IPADDRESS} > ~/ipaddress.txt

```

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> do I need to configure an smtp server like exim4?  I am not really sure how sending mail from your system works.

no you just install mailtutils

your system will send an email to you as

[email]username@servername.domain[/email]

for instance

[email]charles@fileserver.trash[/email]

---

### Post by N00b-un-2 on 2011-12-08
I've probably tried 50 times to send myself an email this morning and I'm not getting anything.  I install mailutils.  How do you reconfigure it after you set it up?  I tried sudo dpkg-reconfigure mailutils and it does nothing.

---

### Post by collisionystm on 2011-12-08
> **Lars Noodén said:**
> The write to the file has to occur after the test if the number has changed.  Otherwise it will never be identified as changed.  Also, [wget]("http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html") is part of the basic distro.

```

#!/bin/bash
IPADDRESS=$(wget -O - www.whatismyip.org 2>/dev/null)
if [ "x${IPADDRESS}" = "x$(cat ~/ipaddress.txt)" ]
then
 exit
else
 echo "Current IP is ${IPADDRESS}" | mail -s "Your IP Address has changed" mail@domain
fi
echo ${IPADDRESS} > ~/ipaddress.txt

```


aaahhhh my mistake. thanks!

---

### Post by collisionystm on 2011-12-08
Except I do believe you want the last echo before the 'fi', correct?

---

### Post by Lars Noodén on 2011-12-08
> **collisionystm said:**
> Except I do believe you want the last echo before the 'fi', correct?

It can go either place, just as long as it is after the comparison.

---

### Post by N00b-un-2 on 2011-12-08
i don't need any help writing the script to query my ip address.  I already had that part figured out and it worked fine.  What I need is to figure out why mail isn't working.

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> i don't need any help writing the script to query my ip address.  I already had that part figured out and it worked fine.  What I need is to figure out why mail isn't working.


cat /var/log/mail.err


post output

---

### Post by N00b-un-2 on 2011-12-08
Dec  8 11:43:46 ryan-1015PE sendmail[19478]: unable to qualify my own domain name (ryan-1015PE) -- using short name


just this over and over

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> Dec  8 11:43:46 ryan-1015PE sendmail[19478]: unable to qualify my own domain name (ryan-1015PE) -- using short name


just this over and over


cat /etc/postfix/main.cf

Check the lines towards the bottom

Here is my output
> 
myhostname = BACKUP.mawaste.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = BACKUP.mawaste.local, localhost.mawaste.local, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
is your hostname correct?

my emails come from [EMAIL="root@mawaste.local"]root@backup.mawaste.local[/EMAIL]

---

### Post by collisionystm on 2011-12-08
oh and do you have a firewall enabled? 

If you have INPUT blocked you need to make sure you have allowed input from your loopback adapter

if you dont have this rule set, it will fail


sudo iptables -I INPUT 1 -i lo -j ACCEPT

---

### Post by N00b-un-2 on 2011-12-08
my host name is the short name for my computer so it's in the wrong format.  At what point should that have been configured because I never did it.

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> my host name is the short name for my computer so it's in the wrong format.  At what point should that have been configured because I never did it.


type 

hostname

in terminal. is the output correct?

---

### Post by collisionystm on 2011-12-08
you should have never configured anything in mailutils

---

### Post by N00b-un-2 on 2011-12-08
ryan-1015pe

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> ryan-1015pe

so does that match what you have in postfix?

---

### Post by collisionystm on 2011-12-08
check your hosts file

> root@BACKUP:~# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    BACKUP.mawaste.local    BACKUP

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


---

### Post by collisionystm on 2011-12-08
Yours could pretty much be


> 127.0.0.1    localhost
127.0.1.1 ryan-1015pe.ryan-pc.local ryan-1015pe

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters 			 		

---

### Post by Lars Noodén on 2011-12-08
Don't you also need a hostname registered in DNS for the machine's mail to be accepted by other hosts?

---

### Post by N00b-un-2 on 2011-12-08
okay, I just edited my /etc/hosts file to look like this

```

127.0.0.1       localhost
127.0.1.1       ryan.1015pe.local ryan

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

and my /etc/postfix/main.cf to look like this

```
myhostname = ryan.1015pe.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = ryan.1015pe.local, localhost.localdomain, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```

---

### Post by N00b-un-2 on 2011-12-08
now this error is reported in /var/log/mail.err

Dec  8 12:12:13 ryan-1015PE sendmail[24502]: unable to qualify my own domain name (ryan-1015PE) -- using short name

---

### Post by collisionystm on 2011-12-08
> **Lars Noodén said:**
> Don't you also need a hostname registered in DNS for the machine's mail to be accepted by other hosts?


no i just checked. my personal computer is not registered in DNS and I was able to send out just fine

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> now this error is reported in /var/log/mail.err

Dec  8 12:12:13 ryan-1015PE sendmail[24502]: unable to qualify my own domain name (ryan-1015PE) -- using short name


what is the output of

cat /etc/mailname

---

### Post by Lars Noodén on 2011-12-08
> **collisionystm said:**
> no i just checked. my personal computer is not registered in DNS and I was able to send out just fine

It was just a vague recollection.  Testing sending from mine, I've tried sending to two different addresses and both SMTP servers are timing out.

---

### Post by collisionystm on 2011-12-08
you also may need to restart postfix

sudo /etc/init.d/postfix restart

---

### Post by N00b-un-2 on 2011-12-08
no such file or directory

---

### Post by collisionystm on 2011-12-08
> **Lars Noodén said:**
> It was just a vague recollection.  Testing sending from mine, I've tried sending to two different addresses and both SMTP servers are timing out.



could your ISP be blocking you somehow?

The only reason I do not think it is a dns issue is because I changed my personal computer to send from the domain charles.linux

I received an email from

[email]charles@charles.linux[/email]

I am on a T2 with static IP's so I know I am not getting blocked ;)

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> no such file or directory


grrrrrr.... hold on, I am going to fire up 11.10 in a virtual machine and see if I can figure out what the H is going on!

I am using Suse on my computer and all of my servers are debian / 10.04 / CentOS

---

### Post by bluexrider on 2011-12-08
ive used no-ip.com in the past for remote, works well

---

### Post by azmyth on 2011-12-08
1. Forward a port to the PC you want to access on your router.
2. Go to No-ip.biz and setup an account
3. Pick a name like blahblah.no-ip.biz and set this to your port in 1.
4. Install the no-ip package from ubuntu. This will check your ip
5. Fill in the values during install
6. Done

This makes life much simpler and you'll never have to worry about it again. I just use blahblah.no-ip.biz to access my home PC using putty, ssh, x2go, nxclient

---

### Post by collisionystm on 2011-12-08
okay it worked from a live cd

here is what I did

first enabled the multiverse, universe repo's to get mailutils

I opened terminal

sudo apt-get install mailutils

It prompted for a Post Fix Configuration

I chose INTERNET SITE

I left the system mail name at Ubuntu

It finished

I ran the command

 echo "Test" | mail -s "This is a test" mail@domaiin

I received an email from Ubuntu@Ubuntu

Test

This is a test

if you have to, remove postfix and mailutils and install again

sudo apt-get purge mailutils

sudo apt-get purge postfix

sudo apt-get install mailutils

^ installing mailutils also installs postfix

---

### Post by collisionystm on 2011-12-08
I checked my mail server logs to make sure the computer did not relay off of it. 

It did not. 

So this should work just fine

---

### Post by collisionystm on 2011-12-08
oh and in case anyone is wondering, my email is through google mail

---

### Post by erind on 2011-12-08
> **collisionystm said:**
> oh and in case anyone is wondering, my email is through google mail

With minimal effort you can use ***ssmtp** *to send mail to gmail. The thing is that it needs your login info in plain text in a config file. But you can create a junk gmail account anytime. That's how I've done it and it works great.

[http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/](http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/)

[http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

---

### Post by N00b-un-2 on 2011-12-08
I just uninstalled mailutils and postfix, rebooted for good measure, reinstalled mailutils, configured postfix and sent a test message to myself...
No email is showing up in my inbox and it's been several minutes.  cat /var/log/mail.err reveals nothing.

---

### Post by N00b-un-2 on 2011-12-08
I'm not running a firewall other than my router itself.  Could be my isp is blocking my email?

---

### Post by collisionystm on 2011-12-08
> **N00b-un-2 said:**
> I'm not running a firewall other than my router itself.  Could be my isp is blocking my email?


If you have no error logs I would say yes, that is the case.

Who is your ISP?

---

### Post by collisionystm on 2011-12-08
I believe most ISP's will block outbound smtp if you are not using an FQDN to send mail.

in my case, I have purchased a static address so my server can be directly on the internet and I can send whatever the heck I want

---

### Post by dmizer on 2011-12-09
> **N00b-un-2 said:**
> Could be my isp is blocking my email?

Most likely. Check here: [http://port25.icannotconnect.com/](http://port25.icannotconnect.com/)

---

### Post by N00b-un-2 on 2011-12-09
my ISP is century link in Phoenix.  All else is configured properly and I attempted this on another computer as well.  Still no outgoing mail yet.  I have checked my router settings and everything should work there.  Is there any way to configure mail to use a different port than 25 and do I need to forward that port?

---

### Post by N00b-un-2 on 2011-12-09
yes, I can confirm port 25 is blocked.  How to I configure mail to use a different port?

---

### Post by N00b-un-2 on 2011-12-09
In the end I just set up an account with no-ip.  I planned on setting up a DNS anyway, but I wanted to see if this script would work.  Unfortunately, my ISP blocks port 25, 587, 2525 and several others commonly used by SMTP to prevent spam I guess.  My only option to get this working at this point is to call them and ask them to open port 25 or just forget about it.

---

### Post by collisionystm on 2011-12-09
> **N00b-un-2 said:**
> In the end I just set up an account with no-ip.  I planned on setting up a DNS anyway, but I wanted to see if this script would work.  Unfortunately, my ISP blocks port 25, 587, 2525 and several others commonly used by SMTP to prevent spam I guess.  My only option to get this working at this point is to call them and ask them to open port 25 or just forget about it.


Or you can buy a domain on go daddy for 10 dollars a year and just send out with that.

You purchase myubuntu.com

you send out as [email]server@myubuntu.com[/email] and it will work.

your isp will allow an FQDN which is house you are able to send from thunderbird / outlook etc.

---

### Post by N00b-un-2 on 2011-12-09
Just out of curiosity, will my DNS work in place of the FQDN?  Obviously for my purposes, ie; trying to email myself my current dynamic external IP address so I could manually update my DNS.  At this point I've determined that postfix simply won't work on my ISP so attempting to email myself just wouldn't work.  But, for the separate objective of getting postfix working, would my DNS work?

---

### Post by dmizer on 2011-12-12
> **N00b-un-2 said:**
> But, for the separate objective of getting postfix working, would my DNS work?

Yes, your DNS domain would work but you'd have to use an SMTP relay. Something like gmail works perfectly for this because it can be configured to send mail as any address you wish. Configuring postfix to use gmail as an SMTP relay is fairly easy if you read the documentation. However, you shouldn't be using straight SMTP on port 25, you should be using ssmtp on port 587 instead. Here's something I dug up on that: [http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)

Edit:
Keep in mind that many email servers will reject your DNS domain as spam when it hits the server, so it may never be sent to any inbox.

---

