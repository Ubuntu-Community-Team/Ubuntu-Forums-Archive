---
title: "Dilemma -- IT War"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by Ha1fDead on 2011-07-14
Hello,

I am currently at war with another IT person at my work office. Somehow he managed to throw a message to my desktop (ubuntu) and I have no idea how he did it. Do any of you have any idea how?

edit: I work at University IT if that is any consolation.

edit2: he is using windows 7 64 bit if any of you have any (nice) throwback ideas.

---

### Post by S.R on 2011-07-14
Have never done it but a little research on Google and I come up with:

He did using the cmd line. More info at  [http://answers.yahoo.com/question/index?qid=20071216012810AAHAi8O](http://answers.yahoo.com/question/index?qid=20071216012810AAHAi8O)

You can...I think ... do it with: ```
  smbclient -M NETBIOSNAME -U FROMNAME 

```

Would like to hear if it worked and what you had to do to get it to work.

---

### Post by Ha1fDead on 2011-07-14
> **S.R said:**
> Have never done it but a little research on Google and I come up with:

He did using the cmd line. More info at  [http://answers.yahoo.com/question/index?qid=20071216012810AAHAi8O](http://answers.yahoo.com/question/index?qid=20071216012810AAHAi8O)

You can...I think ... do it with: ```
  smbclient -M NETBIOSNAME -U FROMNAME 

```

Would like to hear if it worked and what you had to do to get it to work.

If you can tell, i'm a complete Linux noob and I forgot that you can leave messages on the login screen (which is what it was). However, I will find out if that works for some revenge.

Also: how would anyone recommend I "lockdown" my system? I know that he managed to clog my network traffic on my laptop from a DOS. I'm currently running (almost) a standard unbuntu fresh install 10.04.

---

### Post by Ha1fDead on 2011-07-15
bump

---

### Post by haqking on 2011-07-15
> **Ha1fDead said:**
> If you can tell, i'm a complete Linux noob and I forgot that you can leave messages on the login screen (which is what it was). However, I will find out if that works for some revenge.

Also: how would anyone recommend I "lockdown" my system? I know that he managed to clog my network traffic on my laptop from a DOS. I'm currently running (almost) a standard unbuntu fresh install 10.04.

if i was you if another member of staff in a orgranistion IT department is carrying out DOS attacks and such like against you or anyone else in the office then i would go the manager and get it sorted.

hardly professional.

What services are you running ?
Do you have a firewall running (ufw,firestarter etc)

you can block traffic from his machine but that is not the way to carry things out with a work colleague in a IT department.
He sounds like a script kiddie who needs a good talking to ;-)

---

### Post by Ha1fDead on 2011-07-15
> **haqking said:**
> if i was you if another member of staff in a orgranistion IT department is carrying out DOS attacks and such like against you or anyone else in the office then i would go the manager and get it sorted.

hardly professional.

What services are you running ?
Do you have a firewall running (ufw,firestarter etc)

you can block traffic from his machine but that is not the way to carry things out with a work colleague in a IT department.
He sounds like a script kiddie who needs a good talking to ;-)

Haha. I agree that it is unprofessional. However it is mutual, and to report him is to report myself. In lieu of yesterday I installed firestarter (which is 10,000 times better than mcafee from windows). Aside from the firewall how would I secure my computer?

Also, what strict do you think he might have been running (it was from microsoft cmd).

---

### Post by haqking on 2011-07-15
> **Ha1fDead said:**
> Haha. I agree that it is unprofessional. However it is mutual, and to report him is to report myself. In lieu of yesterday I installed firestarter (which is 10,000 times better than mcafee from windows). Aside from the firewall how would I secure my computer?

Also, what strict do you think he might have been running (it was from microsoft cmd).


if it is mutual then what you are asking is how to carry out a IT war.

My advice is stop doing what he is doing and get on with your work.

If he carries on causing you problems then go to manager.

simple.

---

### Post by Ha1fDead on 2011-07-15
> **haqking said:**
> if it is mutual then what you are asking is how to carry out a IT war.

My advice is stop doing what he is doing and get on with your work.

If he carries on causing you problems then go to manager.

simple.

True, but alas that still leaves the vulnerability of my computer in question. I have never truly needed to worry about securing a computer up until this point, and if nothing else this "IT War" is helping my progress my networking abilities in the sense that I am sorting through potential attacks and potential defenses.

IMO common internet defenses were built by hackers (or at the very least scripters) who found vulnerabilities and sought out defenses to them. (Be them white-collar or otherwise is indifferent).

---

### Post by Grenage on 2011-07-15
> **Ha1fDead said:**
> True, but alas that still leaves the vulnerability of my computer in question. I have never truly needed to worry about securing a computer up until this point, and if nothing else this "IT War" is helping my progress my networking abilities in the sense that I am sorting through potential attacks and potential defenses.

IMO common internet defenses were built by hackers (or at the very least scripters) who found vulnerabilities and sought out defenses to them. (Be them white-collar or otherwise is indifferent).

What vulnerability, a DOS?  There's not much you can do about that; heed haqking's advice and let it rest.  Those crackers didn't develop their skills by dossing their workmates and leaving messages on screens; they spend years pen testing, coding and analysing data.

---

### Post by haqking on 2011-07-15
> **Ha1fDead said:**
> True, but alas that still leaves the vulnerability of my computer in question. I have never truly needed to worry about securing a computer up until this point, and if nothing else this "IT War" is helping my progress my networking abilities in the sense that I am sorting through potential attacks and potential defenses.

IMO common internet defenses were built by hackers (or at the very least scripters) who found vulnerabilities and sought out defenses to them. (Be them white-collar or otherwise is indifferent).


there are a few ways to carry out a DOS attack, but it depends on what service of yours he is exploiting.

it may be something as simple as a ping of death

which you can prevent with ICMP filtering on your firewall.

or smurfs,fraggles,teardrop attacks etc etc

A DDOS attack is very hard to prevent.

use some network monitoring software such as wireshark to find out whats happening exaclty.

---

### Post by Tony Flury on 2011-07-15
A DOS attack can have two effects on a networked system : 
1) Excessive memory and CPU usage as the system works to recognise and throw away the excess traffic
2) Usage of network bandwidth (even if the system itself can eject/ignore the incoming traffic)

To protect against the full effects of a DOS attack you need to either : 

1) Have a firewall that is very very good at throwing away unsolicited traffic with miminal processing
2) or a router in front of your system which can do that - and protect your system.

It is worth noting that as well as being incredibly unproffessional, that in many jurisdictions launching any sort of action against another computer system with the purpose of causing either permanent or temporary damage (including something like a DOS attack) could well be a criminal offence.

---

### Post by haqking on 2011-07-15
here read this:

[http://learn-networking.com/network-security/how-to-prevent-denial-of-service-attacks](http://learn-networking.com/network-security/how-to-prevent-denial-of-service-attacks)

but to be honest, let it rest or you are as bad as he is.

---

### Post by NERDMAN! on 2011-07-15
theres nothing wrong with an office war if all it has been is leaving messages on the login screens via command lines. i havent read anything in any of ha1fdead's posts that provides conclusive evidence that it truly is a dos attack. infact to me it sounded more like the guy was using a Disk Operated System not a networking traffic based malicious attack.

and personally i cannot agree with the notion of reporting someone to the boss over some harmless fun. not unless it ends up noticeably interrupting productivity.

ha1fdead would you please clarify exactly what he has done so far and then maybe we can help you come up with an easily fixable prank to get revenge on him with :D

---

### Post by Dangertux on 2011-07-15
In my opinion it is very unprofessional, extremely childish and pretty much just lame. Don't get him back just ignore it or tell your supervisor. 

I'm a little confused though. You say you're a complete Linux noob yet you work in a University IT department? I suppose it isn't really THAT shocking, but to me it sounds like both of you could benefit from stupid pranks less and studying your trade more. 

If he is really attempting to DoS you which is highly immature, turn on syn_cookies, disable ICMP echo-reply, and make sure UDP echo ports are blocked. Unless he is exploiting a known software based DOS (ie: memory leaks, processor hangs , etc) that should help you out a little bit. Look into creating a decent iptables script. Read up on changes you can make to sysctl.conf (this is where syn_cookies settings live)

I find it very childish that you and a colleague who are supposedly professionals are doing this, then when you start losing you come ask us how to win? Come on, don't you have a job to do? You should both go do it. 

I look at this as similar to keying a co-workers car because they got a promotion you wanted. It's stupid, if you wanted it you should work harder.

Just my 2 cents.

---

### Post by haqking on 2011-07-15
> **Dangertux said:**
> In my opinion it is very unprofessional, extremely childish and pretty much just lame. Don't get him back just ignore it or tell your supervisor. 

I'm a little confused though. You say you're a complete Linux noob yet you work in a University IT department? I suppose it isn't really THAT shocking, but to me it sounds like both of you could benefit from stupid pranks less and studying your trade more. 

If he is really attempting to DoS you which is highly immature, turn on syn_cookies, disable ICMP echo-reply, and make sure UDP echo ports are blocked. Unless he is exploiting a known software based DOS (ie: memory leaks, processor hangs , etc) that should help you out a little bit. Look into creating a decent iptables script. Read up on changes you can make to sysctl.conf (this is where syn_cookies settings live)

I find it very childish that you and a colleague who are supposedly professionals are doing this, then when you start losing you come ask us how to win? Come on, don't you have a job to do? You should both go do it. 

I look at this as similar to keying a co-workers car because they got a promotion you wanted. It's stupid, if you wanted it you should work harder.

Just my 2 cents.

+1

Good job they dont work with or for me thats all i can say.

---

