---
title: "Find my router's external IP"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by Roque on 2011-08-27
Sorry for the question but i couldn't find anything relevant so far. My PC is connected to a HW router which in turn is connected to a modem
```

internet-----modem----router----PC1

```
Is there a console command (e.g. in telnet) to get my external (public) IP?
Thanks for any anwers

---

### Post by AlphaLexman on 2011-08-27
I don't know of a local solution, but you can do an internet lookup from a web link inside a terminal...
```
lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | awk '{ print $4 }' | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g'
```
Of course, the '**lynx**' text web browser must be installed.

---

### Post by Roque on 2011-08-28
That's a very useful command, many thanks for your help

But does anyone know if there's a local solution to this? It should be possible (and very basic stuff) to "talk" to the router, which is using pppoe protocol, to get things as the current external IP, connection status, etc.

---

### Post by haqking on 2011-08-28
> **Roque said:**
> That's a very useful command, many thanks for your help

But does anyone know if there's a local solution to this? It should be possible (and very basic stuff) to "talk" to the router, which is using pppoe protocol, to get things as the current external IP, connection status, etc.


log into the router it will tell you in its interface

or you could

ping -R [www.whateverdomain.com](www.whateverdomain.com)

the response after RR: will be your lan followed by your wan ip

---

### Post by Cheesehead on 2011-08-28
To get the answer from the router, you must generally login to the router and scrape the appropriate web page.

Exception: If the modem is running dd-wrt or another linux flavor where you can run bash scripts and muck around in the router's /etc directory. If that's true, then let us know - it's not difficult to create a socket connection between your desktop and the router to feed you this information **if** you have root access.

Since most common routers don't accept telnet connections, does your question indicate that you have reflashed it, or otherwise have root access?

If you want to get the IP address from an external source, an easy way is either of these two commands (they do the same thing):
```
wget -qO - http://automation.whatismyip.com/n09230945.asp
curl http://automation.whatismyip.com/n09230945.asp

```
If you need either command explained, just ask.

---

### Post by Roque on 2011-09-05
Thank for the answers guys
But I'd like to do everything from the bash console, since it is much easier than using the web interface.
> 
Since most common routers don't accept telnet connections, does your question indicate that you have reflashed it, or otherwise have root access?

Not at all, but I set my old modem up (in router mode) using telnet... is it even possible to get the public IP from a router this way? And is it possible to order the router to get a new IP from my ISP?

---

### Post by haqking on 2011-09-05
> **Roque said:**
> Thank for the answers guys
But I'd like to do everything from the bash console, since it is much easier than using the web interface.

Not at all, but I set my old modem up (in router mode) using telnet... is it even possible to get the public IP from a router this way? And is it possible to order the router to get a new IP from my ISP?

between me and cheeseahead above we gave you 3 ways to do it from bash

---

### Post by Roque on 2011-09-06
I thanked you by those but I am looking for a completely local solution, as I'd prefer to not use an external site for such a simple task when my router has all the needed data

---

### Post by spiky001 on 2011-09-06
You will have to install curl but this works ```
curl ifconfig.me/all/json
```

---

### Post by haqking on 2011-09-06
> **Roque said:**
> I thanked you by those but I am looking for a completely local solution, as I'd prefer to not use an external site for such a simple task when my router has all the needed data


So out of interest why cant you 

ping -R whateverdomain

which shows your wan ip, i understand it is going outside but why is that an issue ? unless you didnt have a internet connection of course, but then you wouldnt have a Wan IP then unless it was static, if it was static you would know it anyways ?

or login to the router itself.

Local commands are for Local IP's, your Wan is on a seperate interface so you have to go out to get it

---

### Post by haqking on 2011-09-06
> **spiky001 said:**
> You will have to install curl but this works ```
curl ifconfig.me/all/json
```


That still goes outside as do all the methods given to him so far, he wants it purely local.

---

### Post by SoFl W on 2011-09-06
> **Roque said:**
> That's a very useful command, many thanks for your help

But does anyone know if there's a local solution to this? It should be possible (and very basic stuff) to "talk" to the router, which is using pppoe protocol, to get things as the current external IP, connection status, etc.

```
wget http://automation.whatismyip.com/n09230945.asp
```Will save a file called "n09230945.asp" with just your IP address.
```

wget http://automation.whatismyip.com/n09230945.asp -O - -o /dev/null
```Will print it out in terminal, but the next command prompt will appear after it.


-- EDIT: --
 I see somebody already posted same answer.

---

### Post by Rob_H on 2011-09-06
Bottom line: If you want a "purely local" solution, it depends on the software running on your router.

---

### Post by haqking on 2011-09-06
> **SoFl W said:**
> ```
wget http://automation.whatismyip.com/n09230945.asp
```Will save a file called "n09230945.asp" with just your IP address.
```

wget http://automation.whatismyip.com/n09230945.asp -O - -o /dev/null
```Will print it out in terminal, but the next command prompt will appear after it.

and again is not local, it goes out to whatismyip.com ;-)

---

### Post by nm_geo on 2011-09-06
Yeah even my dd-WRT enabled wireless has an outside connection to Dyndns.org.  So I guess I cheat too..  ;)

---

### Post by haqking on 2011-09-06
You cant see your front door number without opening the door, unless you already know it, if the postman keeps changing it you need to open it from time to time

If you have internet connection then any of the commands shown so far work and no reason to not go outside, or login to router interface, Local IP commands are for the local LAN not the WAN, to communicate with the WAN you need to send traffic across it

If you cant go outside your LAN then you you probably dont have a WAN IP or if its static then should be known already.

Damn im repeating myself ;-)

---

### Post by Roque on 2011-09-28
Thanks for all the help guys

> **haqking said:**
> You cant see your front door number without opening the door, unless you already know it, if the postman keeps changing it you need to open it from time to time

But I had a Linux software router (pppoe) running for years (I used the gateway node also as a workstation), and all i had to do was to grep my IP from ifconfig -a. It was a fully local solution: no need for external sites that could be down eventually, and no annoying long waiting times when the net connection is slowed down due to my ISP's frequent problems. 

Now, my hardware router is also using pppoe so i guess there **ought** be a way to log into it and ask for the current IP, and I imagined that it would be pretty common stuff for most of you. If anyone of you can indeed do this, perhaps you could comment on your router brand/model?

---

### Post by SparTacux on 2011-09-28
I take it you are looking for a telnet solution? Take a look at the telnet commands on your router and see what you can do with it.

---

### Post by haqking on 2011-09-28
> **Roque said:**
> Thanks for all the help guys


But I had a Linux software router (pppoe) running for years (I used the gateway node also as a workstation), and all i had to do was to grep my IP from ifconfig -a. It was a fully local solution: no need for external sites that could be down eventually, and no annoying long waiting times when the net connection is slowed down due to my ISP's frequent problems. 

Now, my hardware router is also using pppoe so i guess there **ought** be a way to log into it and ask for the current IP, and I imagined that it would be pretty common stuff for most of you. If anyone of you can indeed do this, perhaps you could comment on your router brand/model?

Your WAN IP is gonna be either static or dynamic, if it is static then you know it already. So that leaves dynamic, which will only be assigned if you have a connection, if you have a connection then all of the above will work.

from ping -R
to curl
wget

---

### Post by Rob_H on 2011-09-28
> **Roque said:**
> Now, my hardware router is also using pppoe so i guess there **ought** be a way to log into it and ask for the current IP, and I imagined that it would be pretty common stuff for most of you. If anyone of you can indeed do this, perhaps you could comment on your router brand/model?

What is the make and model of the router? Perhaps if someone else here has the same one, (s)he can help you. Otherwise, you should try contacting the manufacturer because there is no universal (cross-router) answer.

---

### Post by Dangertux on 2011-09-28
Ok so as a few have already said, if you want a local solution you have a few alternatives , and they can only occur if your router supports them. 

You mentioned you had a Linux router at one point, you could log into that router, either via telnet or ssh I'm sure. For a local solution you would have to do something along these lines (which has been mentioned already)

You could write a script that logs in via telnet/ssh and basically grabs the ifconfig for the interface in question, and sticks it in a file on your computer and or dumps the output to the console.

You could write a script that logs in via http/https and greps the interfaces page, grabs your external ip and dumps it to a a file on your computer or the console.

As far as internal solutions those are your options. The http/s method will work on most routers even if they don't support telnet, it's going to be a pain, and you're going to have to use something like wget or curl to do it.  However, you would not have to leave the local network in terms of packet traffic.

If that's not good enough then I don't know what you want, because I don't think it exists. As far as how to do either of the above, it depends entirely on what router you have and what services it supports.

---

### Post by Roque on 2011-10-02
Guys, many thanks again for all the answers. This is very enlightening for me :)

> **Dangertux said:**
> 
You could write a script that logs in via telnet/ssh and basically grabs the ifconfig for the interface in question, and sticks it in a file on your computer and or dumps the output to the console.

This is kind of what I had in mind, but It was only a blurred idea, so thanks for the tip on ifconfig. I'll investigate further into invoking ifconfig from telnet 

> **Dangertux said:**
> 
You could write a script that logs in via http/https and greps the interfaces page, grabs your external ip and dumps it to a a file on your computer or the console.

As far as internal solutions those are your options. The http/s method will work on most routers even if they don't support telnet, it's going to be a pain, and you're going to have to use something like wget or curl to do it.  However, you would not have to leave the local network in terms of packet traffic.

So I'd log into my router with http(s), and it would be strictly local? Then I guess there is a http(s) server running into my router.. very interesting, thanks

---

### Post by haqking on 2011-10-02
> **Roque said:**
> Guys, many thanks again for all the answers. This is very enlightening for me :)


This is kind of what I had in mind, but It was only a blurred idea, so thanks for the tip on ifconfig. I'll investigate further into invoking ifconfig from telnet 


So I'd log into my router with http(s), and it would be strictly local? Then I guess there is a http(s) server running into my router.. very interesting, thanks

All of this would work, but it means connecting to your router which i what i said in my first response in post #4

Just connect to your routers interface and it will tell you the WAN IP, same as Telnetting into it.

just go to x.x.x.x IP address in your address bar and log into it.

Which has been said already

---

### Post by Roque on 2011-10-02
> **haqking said:**
> All of this would work, but it means connecting to your router which i what i said in my first response in post #4

Just connect to your routers interface and it will tell you the WAN IP, same as Telnetting into it.

just go to x.x.x.x IP address in your address bar and log into it.

Which has been said already
That would mean firing up the browser, logging into the router, switching to the right tab in the web interface, etc. Too slow, plus this way you can't automatize any further task involving the obtained IP

Anyway, it's solved now (locally and fully automatically). Many thanks to all for your kind help

---

### Post by se4n_1 on 2012-01-17
How did you solve it in the end?

---

### Post by kevdog on 2012-01-18
This thread was originally written like 1 year ago.  I'm highly doubting the guy is going to answer.

---

### Post by haqking on 2012-01-18
> **kevdog said:**
> This thread was originally written like 1 year ago.  I'm highly doubting the guy is going to answer.

5 months ago and the OP last reply was 3 ;-)

oh and was last active 2 weeks ago.

no reason why the OP wouldnt respond to their own thread whenever it was created, i know i do.

---

### Post by ikarpenis on 2012-04-20
This is my quick and simple solution in perl (set proxy server if you have one):

```
#!/usr/bin/perl

use LWP::UserAgent;

################################################################################
    
    my $page       = '[COLOR=Sienna]http://checkip.dyndns.org[/COLOR]';
    
    my $use_proxy  = 1;
    my $proxy      = 'proxy_string';
    my $proxy_port = '80';
    my $username   = 'username_string';
    my $password   = 'password_string';
    
################################################################################


my $browser = LWP::UserAgent->new;

if($use_proxy == 1){
    $browser->proxy('http', "http://$username:$password\@$proxy:$proxy_port/");
}

my $response = $browser->get("$page");

die "\n\nError: ", $response->status_line, "\n\n" unless $response->is_success;

my $output = $response->content;

my ($external_ip) = ($output=~/Current IP Address: (\d+\.\d+\.\d+\.\d+)/);

print("\n\nExternal IP: $external_ip\n\n");

exit(0);
```


You can place the script in any server in your private network to work.

---

