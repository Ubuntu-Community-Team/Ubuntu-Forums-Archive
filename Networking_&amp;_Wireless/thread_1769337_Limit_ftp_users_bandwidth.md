---
title: "Limit ftp users bandwidth"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2011-05-27
I'm running an ftp server file to serve to some close friends and family. Each person has there own user profile on my system. What I want to know is, is it possible to limit the amount of bandwidth that each user can use so that they don't chew up all my Internet usage. So for example limit each user to 2GB of data.

I've tried looking this up the closest that I could find is disk quota limits which is not what I'm after.

---

### Post by Jonny87 on 2011-05-28
I'm thinking that if i could get some sort of finding the usage for userX that outputs to something simple like
7890
then I could run something like the following;
> 
if [ $(*quota-command*) -gt 8000 ]; then
iptables -A OUTPUT -o ethX -m owner --uid-owner {USERNAME} -j REJECT
fi
Even if there was a way to output the usage to a text file then read from that.

yes?? no??? anyone???

---

### Post by Lars Noodén on 2011-05-28
The supplementary documentation (HOWTOs, Tutorials, etc.) for IP Tables are rare and approaching 10 years old.  So it is hard to find material to answer this question.

It looks like it might be possible to limit the speed using [hashlimit](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#HASHLIMITMATCH).  

[quota](http://linux.die.net/man/8/iptables) can limit the overall bandwidth consumed.

Between the two, you might be able to achieve what you are proposing.

---

### Post by Jonny87 on 2011-08-19
*BUMP*
I'm still trying to find a way of achieving this, still looking into the suggestion above but not sure on it.

I'm running VSFTP and want to put a limit on the amount that each user can upload and download. Say for example 2GB, then once the limit is reached it will cut off there internet usage or drop their speed right down to something ridiculously slow. Kind of like an ISP does. As I don't know all the IP's of each user as most do not have static IPs, it needs to be a per user base system for each user on the server and still apply when they sign in via VSFTP.

I'm not so interested in limiting the speeds so much but just the overall bandwidth.

Does anyone know of an application or a script that can do this? I'm still learning some of this side of Linux so I'd appreciate it if people could include an example of commands when suggesting something.

Thanks in advanced for any help that you can provide.

---

