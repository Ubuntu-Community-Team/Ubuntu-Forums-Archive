---
title: "Torrent is downloading but cant browse any site."
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by fezar.fz on 2011-09-01
Hey there, I can download files through torrent but cant browse any site. I am using 10.10 and firefox, connecting through VPN.

---

### Post by fdrake on 2011-09-01
> **fezar.fz said:**
> Hey there, I can download files through torrent but cant browse any site. I am using 10.10 and firefox, connecting through VPN.

check your firefox preferences > network : do you have manual proxy enabled?

---

### Post by fezar.fz on 2011-09-01
Thanks for the reply, yes i checked the network proxy, its is ticked on direct.

Is there a problem with my browser?

---

### Post by fdrake on 2011-09-01
you may have port 80 or 8080 disabled somehow.
does this happen only with firefox or with other browsers?

---

### Post by sanderj on 2011-09-01
> **fezar.fz said:**
> Hey there, I can download files through torrent but cant browse any site. I am using 10.10 and firefox, connecting through VPN.

What kind of VPN? A corporate VPN? If so, are you allowed to browse at all? Or do you need to use proxy server?

When you type "wget www.google.com" in a terminal, what's the result?

---

### Post by fezar.fz on 2011-09-01
@fdrake it is happening with chrome as well. How can i enable these ports you are talking about?

@sanderj it is a home vpn, i can use internet on windows xp and is working fine. But on ubuntu vpn is connecting but only torrent files are downloadable. I will show u the output of the command.

---

### Post by fezar.fz on 2011-09-01
nett@ubuntu:~$ wget [www.google.com](www.google.com)
--2011-09-01 16:25:35--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.google.com](www.google.com)'
nett@ubuntu:~$

---

### Post by sanderj on 2011-09-01
> **fezar.fz said:**
> nett@ubuntu:~$ wget [www.google.com](www.google.com)
--2011-09-01 16:25:35--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.google.com](www.google.com)'
nett@ubuntu:~$

That could be a name-resolving problem. So next command line tests in terminal:

wget 74.125.79.147

and

mtr -n -r -c4 8.8.8.8

and:

in firefox, can you open [http://194.109.6.92/](http://194.109.6.92/) ?

---

### Post by fezar.fz on 2011-09-01
nett@ubuntu:~$ wget 74.125.79.147
--2011-09-01 18:26:29--  [http://74.125.79.147/](http://74.125.79.147/)
Connecting to 74.125.79.147:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.1'

    [  <=>                                  ] 9,845       28.0K/s   in 0.3s    

2011-09-01 18:26:30 (28.0 KB/s) - `index.html.1' saved [9845]

nett@ubuntu:~$ mtr -n -r -c4 8.8.8.8
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 111.119.186.1                 0.0%     4    6.4   6.7   5.5   8.1   1.1
  2. 192.168.20.2                  0.0%     4    6.4   5.8   4.1   6.9   1.2
  3. 221.120.249.1                 0.0%     4    6.3   6.7   5.5   8.0   1.1
  4. ???                          100.0     4    0.0   0.0   0.0   0.0   0.0

---

### Post by fezar.fz on 2011-09-01
Yes I can browse that site xsomething4all.com...

---

### Post by sanderj on 2011-09-01
I think the problem on your system is that name resolving isn't working. So, your system does not know how to convert "www.google.com" into an IP address.

Easy check:

"host www.google.com"

and

"cat /etc/resolv.conf"

which is probably empty, or not functioning.


Also type:

"host [www.google.com](www.google.com) 8.8.8.8"

to see if you reach that nameserver.



To solve this, there are a few methods: quick-and-dirty, more beautiful, or with a good analysis first. What do you want?

---

### Post by fezar.fz on 2011-09-03
Well I think 'quick' method will be just fine for me..terminal cant resolve "host www.google.com" and neither can "host [www.google.com]("http://www.google.com/") 8.8.8.8", where as resolv.conf is not empty and showing things correctly..please let me know the solution..?

---

### Post by sanderj on 2011-09-03
"host [www.google.com](www.google.com) 8.8.8.8" should work, otherwise I have no solution for you. What's your output?

And post the output of /etc/resolv.conf

---

