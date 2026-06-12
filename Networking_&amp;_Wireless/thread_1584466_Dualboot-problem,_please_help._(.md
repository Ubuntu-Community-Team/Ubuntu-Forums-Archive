---
title: "Dualboot-problem, please help. :("
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by jacobjul on 2010-09-29
Hi there, 
I recently managed to dualboot ubuntu with vista on my laptop and it worked wonders for a few days...

However, 
after installing some updates while on linux I am now unable to access the Internet when using vista. Internet is still accessible from linux, and vista can connect to the local network. I'm using a wired connection.

The reason I think it's because of linux is:
When I woke up yesterday I logged onto vista and had internet, then rebooted with linux got an update-pack at around 100-120MB, installed those and rebooted back into vista... Internet gone.

I'm a complete scrub when it comes to linux, I decided to dualboot with it because I currently study Haskell at school and programming Haskell on windows is a *****.

Tried the sweclockers forum and linuxforums.org, and although many people have tried to help me I have yet to make any progress . :(

I've had my share of problems with vista solved most of them, worked around the other, but not me nor the people who tried to help me could find any problems with my windows settings.

Been at it for 16 hours and counting (not including 6h of sleep)... wish I was exaggerating.


I am desperate, please help me. :confused: :confused:
I'll be stalking this thread until I fix this.

PS sorry about the wall of text.

---

### Post by psavva on 2010-09-29
Firstly, you need to realize 2 things:
1) Ubuntu is an Operating System like Windows Vista.
2) Ubuntu settings/updates/etc cannot and does not interfere with Vista's settings/functionality/etc..

So with that said. The updates on Ubuntu did not, and could not cause the fact you don't have internet on Visa.  This is a pure 100% Vista problem... You won't find the answer in Linux...  

Try checking if you Network Card is enabled in Vista.
I also suggest calling your internet service provider as to help you trouble shoot the problem...

---

### Post by jacobjul on 2010-09-29
> **psavva said:**
> Firstly, you need to realize 2 things:
1) Ubuntu is an Operating System like Windows Vista.
2) Ubuntu settings/updates/etc cannot and does not interfere with Vista's settings/functionality/etc..

So with that said. The updates on Ubuntu did not, and could not cause the fact you don't have internet on Visa.  This is a pure 100% Vista problem... You won't find the answer in Linux...  

Try checking if you Network Card is enabled in Vista.
I also suggest calling your internet service provider as to help you trouble shoot the problem...

I've checked my card, all my settings, I've conntacted my provider. Nothing helped I've dealt with Vista before, but everything is like it should be. 

I updated linux (where I had no access to internet), and then suddenly linux had access to internet while vista didn't. 

Too many stars have aligned for it to just be a coincidence.

I definitely have less of a clue than any of you but please if there is ANY chance whatsoever that this is related to me updating linux please help me. 

I've tried every fix google have given me after 17h short of a complete reinstallation of vista. :(

---

### Post by grahammechanical on 2010-09-29
I have absolutely no experience with Vista, except when I visited my sister a few months ago and had look at her vista laptop. I am also fairly new to linux. I am not much help but I do sympathise. 

I visit this forum and I see many posts from people not getting an internet connection after upgrading Ubuntu but it is always Ubuntu that they cannot connect with. There always say that they can connect fine with Vista or Windows 7. You have the opposite problem and you blame Ubuntu. That is frustrating to those of use who are trying to help solve problems.

May I suggest that you try to think of this by going back to first principles? Check everything as from the beginning. What messages do you get in Vista? What system utilities does Vista use to connect to the internet? Things like that. 

regards

---

### Post by jacobjul on 2010-09-29
> **grahammechanical said:**
> I have absolutely no experience with Vista, except when I visited my sister a few months ago and had look at her vista laptop. I am also fairly new to linux. I am not much help but I do sympathise. 

I visit this forum and I see many posts from people not getting an internet connection after upgrading Ubuntu but it is always Ubuntu that they cannot connect with. There always say that they can connect fine with Vista or Windows 7. You have the opposite problem and you blame Ubuntu. That is frustrating to those of use who are trying to help solve problems.

May I suggest that you try to think of this by going back to first principles? Check everything as from the beginning. What messages do you get in Vista? What system utilities does Vista use to connect to the internet? Things like that. 

regards

inb4 reply
I'm sorry if I somehow offended you by blaming ubuntu here. :(

Anyways,

If I try to repair my connection in vista I get the error:
Could not communicate with Primary DNS-server(numbers)
Everything else checks out fine.

I tried not to blame ubuntu vista is ****. 
But I just can't find anything wrong with my settings nor could sweclockers forums. I've tried to reset and fix every single dns/ip/network card. I have tried several different connections wrired/wifi, I tried the net at school... without any change. 

Fact is that after I was able to get ubuntu's net working I lost it on vista. (After the ubuntu update and a reboot) 

Yes, I am having the complete opposite problem that many has with ubuntu not connecting. But doesn't that just make the chance that it is actually ubuntu that is the cause in this case?


Im open to any suggestions ubuntu or vista. :/

---

### Post by grahammechanical on 2010-09-29
I just tried to send you a reply but it was so long that my session time out and when I came to send the reply it disappeared because I was log out.

As I understanding it the Primary DNS server address is the location of the ISP computer/server that we connect to to gain access to the Internet. If the modem does not have the correct DNS address the the Operating System cannot connect to the internet. But Ubuntu does. How so, when Vista doesn't?

Could Ubuntu be connecting to a different network? could it be connecting automatically to a nearby unsecured wireless network? I am just trying to think of something to help. Think of any thing.

Have you reset the router and so put the setting back to the factory default settings. So, the router does not know the Primary DNS address of your ISP servers?

Regards.

---

### Post by grahammechanical on 2010-09-29
Sometimes when we try to fix one problem we do so many things and we cause another problem and we go on trying to fix the first problem when it is another problem that needs to be fixed first.

Can you access the set-up program in the modem? To check that it has the correct settings? Yes, I know that you have done that but what can I say? You still need help and what are we coming on this forum for, if not to try to help?

Regards.

---

### Post by jacobjul on 2010-09-29
> **grahammechanical said:**
> I just tried to send you a reply but it was so long that my session time out and when I came to send the reply it disappeared because I was log out.

As I understanding it the Primary DNS server address is the location of the ISP computer/server that we connect to to gain access to the Internet. If the modem does not have the correct DNS address the the Operating System cannot connect to the internet. But Ubuntu does. How so, when Vista doesn't?

Could Ubuntu be connecting to a different network? could it be connecting automatically to a nearby unsecured wireless network? I am just trying to think of something to help. Think of any thing.

Have you reset the router and so put the setting back to the factory default settings. So, the router does not know the Primary DNS address of your ISP servers?

Regards.

Im using the same router to type this and I've reset it many time... many many times... :( , also I have my wireless card off :/

---

### Post by grahammechanical on 2010-09-29
Jacobjul

I am trying hard to be some kind of a genius and you are naking it so difficult for me. :):)  I am beginning to doubt my own powers of genius-ness. Have you actually set up dual-boot system? Or did you use something called Wubi? This lets you install Ubuntu from with-in Vista. I am unfamilar with this way of running two operating systems. But if something is blocking Vista from Internet access and it is not the wrong settings in the modem and Vista can reach as far as the modem as can Ubuntu, then how is it possible for one OS to access the physical ports on the computer and another be unable to do so? This is not logical, as a Vulcan would say. Is there a firewall?

Regards

---

### Post by grahammechanical on 2010-09-29
Jacobjul

I have just had another thought. In Ubuntu we can set up different users and can deny them access to various functions/services such as internet connection. In Vista can you do the same? Are you logging on with sufficient access?

Regards

---

### Post by jacobjul on 2010-09-29
Don't we all love it when the vulcans logic fails? :p

On a more serious note:
Yes it is proper dualboot, No OS-within-OS-software involved, and the first thing I did was kill all firewalls/security programs.

---

### Post by oldfred on 2010-09-29
Have you tried a cold boot? I have seen (not personally ) where a modem card retained a setting that was not reset correctly on  a warm reboot.

What modem are you using and does it have any other issues?

---

### Post by lfforman on 2010-09-29
In regards of your problem I agree that is frustrating, but, since you are dual booting, cannot be an ubuntu problem.

trying to help you with windows vista.

the first clue is the DNS error message. 

1 - did you checked your network properties on windows? are you using a fix ip addres or using a dhcp from the router?

if you are using a fix ip address try to see the ip address wich ubuntu is getting on the network including gateway and dns. note them down.

go to windows and check if the dns and gateway are the same as ubuntu. if they are not try to force them putting the same configuration as ubuntu and see if this solve the problem.

another option is openning a comand prompt (as administrator) in widows and type ipconfig /release and then ipconfig /renew
and see if this solve your problem.

Another possibility is that you have something broke in widows and some network service is not running properly, i do not remeber all the services names, but u can check it on a windows forum.

Other possibility is to force a different dns you could use google dns that is 8.8.8.8 or check opendns.org and see if with that dns you can use the internet.

do your service provider have any type of rule for avoid use of more then one computer in the same address? the rule they set up could be causing you not being able to connect in windows, i suggest that you get in touch with them and see if this could be the reason.

---

### Post by jacobjul on 2010-09-30
@ Ifforman, I've tried all your advices, and yesterday I reinstalled vista. No-Change. Feels awesome :)

I've been on several different networks(all operational) both wireless and wired. Only local :)

---

### Post by lfforman on 2010-10-01
when you reinstalled the vista did you made a clean installation or you just installed in top of the one with problems? If you did the second option you could try to completely format the Windows Partition. some times when you install a windows in top of the other you do not clean all the registers, dlls and drivers installed.

I could give you another suggestion is to completely remove the windows partition use ubuntu as primary system and install a virtual machine with vista.

---

