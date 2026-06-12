---
title: "apt happy with proxy-server access but browsers not"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by TonyGould on 2013-01-10
Hi,

I need to access the internet using a proxy server, which requires my windows username and password. I'm having trouble getting this to work: strangely, apt, systems update etc works just fine, whereas browsers, and possibly other applications too, fail.

I configured my /etc/apt/apt.conf and /etc/environment according to some very helpful posts on these forums. My apt.conf is
```

Acquire::http::proxy "http://WINDOMAIN\WINUSER:WINPASSWORD@URL:8080/";
Acquire::https::proxy "https://WINDOMAIN\WINUSER:WINPASSWORD@URL:8080/";
Acquire::ftp::proxy "ftp://WINDOMAIN\WINUSER:WINPASSWORD@URL:8080/";
Acquire::socks::proxy "socks://WINDOMAIN\WINUSER:WINPASSWORD@URL:8080/";

```

But when I use the equivalent syntax in /etc/environment (omitting the "Acquire::"), firefox and chrome won't connect; in fact they pretty much hang. For the moment, I'm running without the doman\user and password in /etc/environment and firefox does eventually come back with a request for the username and password, and then seems to get something back from the server before stopping again. To be clear, as I dropped the user & password from /etc/environment as it wasn't helping, I now get this in a terminal
```

tony@precise:~$ echo $http_proxy
http://URL:8080/

```
The issue *may* be that I'm running under a virtual machine, under virtualbox to be precise (I've seen the same issue with vmware as well). I'm using 12.04 and have seen the same problems with unity and with classic gnome, which I'm running now.

I can't change the network settings in windows, but my feeling is that virtualbox (using the NAT option) should behave just like a regular windows application from the proxy server's point of view. This view is supported by the fact that apt works without any problems whatsoever (and when I used the alternate installer, I typed in the proxy server settings during the installation process, and the installer was able to download all the updates during installation).

I've also tried running chrome using the command-line proxy-server setting and configuring firefox Edit/Preferences network connection to be the same as in my host Windows Tools/Options, but this doesn't seem to help.

My knowledge of networking is very limited, so the following may not be at all relevant, but in case it helps I get the following in a terminal.
```

tony@precise:~$ host google.com
google.com has address 173.194.34.174
google.com has address 173.194.34.167
google.com has address 173.194.34.161
google.com has address 173.194.34.160
google.com has address 173.194.34.168
google.com has address 173.194.34.164
google.com has address 173.194.34.165
google.com has address 173.194.34.166
google.com has address 173.194.34.162
google.com has address 173.194.34.163
google.com has address 173.194.34.169
google.com has IPv6 address 2a00:1450:4009:805::1005
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.

```

hopefully someone can point me in the right direction.

atb,

Tony.

---

