---
title: "Host Lookup Order?..."
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2010-09-07
I have a internet registered IP.  And for right now until I complete the development site I have it pointing to a holding website which is my office live site.  There I have the default page saying the "Site Is Under Maintenance?.

My problem is, on my server I need to update some Drupal Modules, but when I enter my registered IP Name which is defined in my "host" file as 127.0.0.1, but I keep hitting my holding site.

On my development system I can hit my server when I enter my Reg IP Name which is defined in the "host file 192.168.1.74 pointing to my server.

Is it possible to have it look at the host file first before checking the internet DNS?

---

### Post by MaindotC on 2010-09-07
I'd really like to help you with this but you're using some terms that I think are misleading - it's nothing bad it's just that I need to clarify some things with you.  First of all, what do you mean when you say an "Internet registered IP"?  Do you mean domain name?

127.0.0.1 is referred to as a "loopback" address or "localhost".  If you look in your /etc/hosts file by default there is usually a line that says this:```
127.0.0.1	localhost
```  You cannot access any webserver using this address other than the one running (if you have one) on the machine in which you are operating.  So, it was a little difficult to understand exactly your setup but it seems to me that you may be trying to access another machine using 127.0.0.1 and that won't work.

Then you mention a "reg ip name" that is defined as 192.168.1.74.  Just like 127.0.0.1, this is an address that is in a range of addresses reserved for non-routable addresses.  That means they can only be used on a local network of machines and you cannot access a machine on a different network using an address in this range.  That's not entirely true but please bear with me.  So anyway, you cannot access a machine in the 192.168.x.x range anywhere on the Internet, especially if you are accessing the machine from a home network that has an access point or gateway.

I'd really like to help you with this because I'm a networking professional and I'm slowly learning drupal so I think we have opposite roles and could help each other :D  Here are some questions I need answered:

From where are you trying to access other machines? (home network with an access point or what is incorrectly called a router)  

What is the ip address of the machine you are using to access the other machines? (if it's in the 192.168.x.x range you will have to modify some settings on your access point)

What is the ip address of the machine that needs the modules updated?  Does it have a domain name or are you viewing it in your browser by typing in the ip address?

It may be a little quicker and convenient for us to discuss this in irc.  You can reach me in #ubuntu-us-ny or #drupal.  I have different screen names so just ask if strAlan is there.  I apologize if I don't immediately reply but I'll look for you there and we can get the gist of this sorted out without playing forum-post-tag.

---

### Post by Hobgoblin on 2010-09-07
> **VcDeveloper said:**
> 
Is it possible to have it look at the host file first before checking the internet DNS?

In answer to this question.

The default is to check the hosts file before using DNS.

---

### Post by VcDeveloper on 2010-09-08
Oh yea, it does sound a bit confusing huh!  Ok, let me clear this up a bit.

1) I have my own server for hosting Drupal CMS.
2) Yes, I meant Domain Name and my Registrar has my IP pointing to my server and AT&T as my ISP.
3) I have another Domain Name with MS Office Live just to use as a holding site for when I need to take the site off line.

For example my Domain Name is myname.com, in my server host file I have:
127.0.0.1 myname.com  [www.myname.com](www.myname.com)

when I type myname.com in the browser I'm being sent to my hold site.  On my development computer which is connected to the internet and the my network, and I type myname.com in the browser it send me to my server as expected.

So, I'm wondering why it doesn't do this on my server?

---

### Post by MaindotC on 2010-09-08
Ok let me see if I understand this.  Some of it is repeating what you said so forgive me for reiterating.

The MS Office Live site (we'll just call it "Live site") is hosting a "Under Construction" site.  You set the domain registrar to point [www.myname.com](www.myname.com) to the Live site, correct?

Your developing your Drupal installation on your home machine (or one of your home machines) and when you want that site displayed, you set the domain registrar to point [www.myname.com](www.myname.com) to the public ip address of your home network (which represents all the machines on your home network), correct?

Now you have a 2nd machine on your home network that you are using to test what appears when you go to [www.myname.com](www.myname.com) and for some reason it is showing the Live site instead of the Drupal installation also on your home network, correct?  You want to make sure when someone goes to your website it goes to the Drupal install and not the Live site, correct?

The server host file appears to be correct, although for some reason in mine I had to put the public ip address in that file.  That machine, the one holding your drupal installation, should always show your drupal installation because it should check its own /etc/hosts file and say "oh I know where [www.myname.com](www.myname.com) is - right here on the local machine - so I have no need to send out a DNS request for it's IP address."

The machine that is still showing the Live site could be showing that because DNS records take 24-48 hours to update.  This is a configuration that is set in DNS configuration files and I believe the registrar should tell you this when you modify their host record.  Did you change it recently?  Another troubleshooting method you can take to see what's going on is perform an nslookup of your domain name (or website).  That will show you what records the registrar is holding.  If you do an nslookup for you website and you get the ip address of your public ip address, which represents the server with the Drupal installation, then you are receiving the correct records and so will anyone else accessing your website.  If you are still receiving the ip address for the Live site then the registrar has not updated it's DNS records yet.

Also, did you know in Drupal you can go to Site Configuration -> Site Maintenance and select an option to take the site offline while you update/install modules?

---

### Post by VcDeveloper on 2010-09-08
> **strAlan said:**
> 
The MS Office Live site (we'll just call it "Live site") is hosting a "Under Construction" site.  You set the domain registrar to point [www.myname.com]("http://www.myname.com") to the Live site, correct?


Yes!

> **strAlan said:**
> 
Your developing your Drupal installation on your home machine (or one of your home machines) and when you want that site displayed, you set the domain registrar to point [www.myname.com]("http://www.myname.com") to the public ip address of your home network (which represents all the machines on your home network), correct?


Yes!

> **strAlan said:**
> 
Now you have a 2nd machine on your home network that you are using to test what appears when you go to [www.myname.com]("http://www.myname.com") and for some reason it is showing the Live site instead of the Drupal installation also on your home network, correct?  


No, it does this on my server.  The server is where I want to update the production modules of Drupal.  So I have to display the site on the server and go to the admin pages to do this.  My development computer does as expected when I type myname.com it displays the website on the server.

> **strAlan said:**
> 
You want to make sure when someone goes to your website it goes to the Drupal install and not the Live site, correct?


Only when the site is on-line.  If I take it off-line then they will be redirected to the MS Office site which only displays "Site Off-Line.......". 

> **strAlan said:**
> 
The server host file appears to be correct, although for some reason in mine I had to put the public ip address in that file.  That machine, the one holding your drupal installation, should always show your drupal installation because it should check its own /etc/hosts file and say "oh I know where [www.myname.com]("http://www.myname.com") is - right here on the local machine - so I have no need to send out a DNS request for it's IP address."


Correct, but for some reason it sending me to my off-line site.

> **strAlan said:**
> 
The machine that is still showing the Live site could be showing that because DNS records take 24-48 hours to update.  This is a configuration that is set in DNS configuration files and I believe the registrar should tell you this when you modify their host record.  Did you change it recently?  


Made no changes.

> **strAlan said:**
> 
Also, did you know in Drupal you can go to Site Configuration -> Site Maintenance and select an option to take the site offline while you update/install modules?

Yes! I have the other off-line site just in case the server goes down or needs upgrading.

---

### Post by MaindotC on 2010-09-08
Ok, so the server holding the drupal installation is not properly resolving the domain name for the very same content it is hosting.  I don't see how that's possible seeing as how other machines can access it but ok we'll just go w/ that.

I believe you need to edit the /etc/hosts file on the Drupal server so it knows it is holding the contents for [www.myname.com](www.myname.com).  I cannot give you a definitive answer on how to do this, but I did it for my machine and I just kind of magically got it to work.  I googled a lot on how to change the host name of your machine and so forth but I didn't really document my steps.

Here's an example of my hosts file that is holding a drupal installation on [http://drupal.manner18.com](http://drupal.manner18.com) (which is a development environment for a site I'm interested in creating).```
127.0.0.1	localhost.localdomain	localhost
24.59.254.92	www.manner18.com
```
As you can see, I have the localhost and localhost.localdomain names resolving to the 127.0.0.1 address because I don't want my machine querying any DNS servers - I just want it to "loopback" to it's self (then apache will handle the http request).  I put in the public ip address and the domain name.  I believe my domain name was not resolvable without this entry.  Even though the machine is on a home network, with an ip in the 192.168.x.x range, I still needed to tell it this.  Obviously I have my AP configured to forward any requests for port 80 to be served by this machine.

I tested this by commenting the public ip address and restarting networking, but it still works.  I'm not sure if that's a caching issue, or if it's b/c I'm not able to test it from another public ip, or if it takes time to update.  

I'm sorry for such horrible directions but that being said, it appears to be a problem with the Drupal server improperly resolving it's own host name.  I guess I just never anticipated running into this problem in the future once I got it all set up.  Which is what Hobgoblin said and apparently he has a better ability for understanding what happened than I do :(

Was it working before and something happened and all of a sudden the Drupal server wasn't responding properly?

---

### Post by Hobgoblin on 2010-09-09
> **VcDeveloper said:**
> 
when I type myname.com in the browser I'm being sent to my hold site.  On my development computer which is connected to the internet and the my network, and I type myname.com in the browser it send me to my server as expected.

So, I'm wondering why it doesn't do this on my server?

Let me get this straight.  You are logged onto your server, and type the address into a web browser running on the server.  The hosts file on the server is set to direct the url to 127.0.0.1 yet you are getting to the server located on the internet.

Try pinging the domain name from the server, see what IP address it is resolving to.

Double check the hosts file on the server for typos.

---

### Post by VcDeveloper on 2010-09-09
> **Hobgoblin said:**
> Let me get this straight.  You are logged onto your server, and type the address into a web browser running on the server.  The hosts file on the server is set to direct the url to 127.0.0.1 yet you are getting to the server located on the internet.


Yes!

> **Hobgoblin said:**
> 
Try pinging the domain name from the server, see what IP address it is resolving to.


This is confusing because I get the correct hit when I ping:
PING mydomain.com (127.0.0.1) 56(84) bytes of data.
64 bytes from DrupalWebserv1 (127.0.0.1): icmp_seq=1 ttl=64 time=0.045 ms

Is there something wrong with FireFox 3.6.9?  Also I'm running Ubuntu 9.10 Karmic

> **Hobgoblin said:**
> 
Double check the hosts file on the server for typos.

This is what I have in the host file:
127.0.0.1    DrupalWebserv1    localhost.localdomain    localhost
127.0.0.1    mydomain.com        [www.mydomain.com](www.mydomain.com)
127.0.1.1    DrupalWebserv1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by MaindotC on 2010-09-09
> **VcDeveloper said:**
> This is confusing because I get the correct hit when I ping:
PING mydomain.com (127.0.0.1) 56(84) bytes of data.
64 bytes from DrupalWebserv1 (127.0.0.1): icmp_seq=1 ttl=64 time=0.045 ms

Is there something wrong with FireFox 3.6.9?  Also I'm running Ubuntu 9.10 Karmic



This is what I have in the host file:
127.0.0.1    DrupalWebserv1    localhost.localdomain    localhost
127.0.0.1    mydomain.com        [www.mydomain.com](www.mydomain.com)
127.0.1.1    DrupalWebserv1


It's definitely not Firefox that is causing the problem...believe me THAT is not the problem here.  Anyway, if you just want to eliminate that possibility use a different browser.  Regardless of that, Firefox is using the same tool to get the ip address associated with your domain name as ping does.  So when you type your domain in Firefox it should issue a request and first consult your /etc/hosts file and see that it's right there and no need to send a request to a dns server.  If you wanted, you could make your hosts file point google.com to your localhost and then every time you typed in FF google.com it should resolve to your machine.

What is your domain anyway - I want to check it myself.

---

### Post by VcDeveloper on 2010-09-10
> **strAlan said:**
> 
What is your domain anyway - I want to check it myself.

[thegardenofedenblessing.com]("http://thegardenofedenblessing.com") - when you type this in, it will send you to my MS Office Site gardenofedenblessing.com

---

### Post by MaindotC on 2010-09-10
Ok we're going to do this step by step.  The ip address I get is 174.129.88.121.  Is that the public ip address of the Drupal machine? (I'm guessing not).

---

### Post by VcDeveloper on 2010-09-10
No, it's my Registrar IP with [NO-IP.com]("http://NO-IP.com").  I have a Control Panel where I can set certain options and one of theme is redirection which is set to my MS Office site until I go back live.

---

### Post by MaindotC on 2010-09-10
Ok...I'm not familiar with this no-ip business but change it back to the ip address of the server you want to see.

---

### Post by VcDeveloper on 2010-09-13
Uhmmm, I was working on another configuration for something else and restarted Apache and now it's working!

---

### Post by MaindotC on 2010-09-13
Please mark the thread as solved and edit your first post to state "Update:" and the solution so other users do not have to read the entire thread.

---

