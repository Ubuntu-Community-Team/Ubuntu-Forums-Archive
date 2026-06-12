---
title: "use proxy globally in ubuntu 11.04?"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2011-09-02
I'm trying to set up my ubuntu system to use TOR globally, in all applications, but I can't seem to find any instructions for the newer releases, so everything I find it years out of date. Right now, I have TOR installed from the TOR repositories, as well as privoxy. I followed this set of commands, which don't seem to make much sense anyway. 

```


[LIST=1]
[*]sudo aptitude install tor
[*]sudo  vim /etc/tor/torrc
[*]sudo  vim /etc/privoxy/config
[*]comment out: &#8220;logfile logfile&#8221; and &#8220;jarfile jarfile&#8221;
[*]find: listen-address 127.0.0.1:8118
[*]add (on next line): forward-socks4a / localhost:9050 . (including the period)
[*]sudo /etc/init.d/tor restart && sudo /etc/init.d/privoxy restart
[/LIST]

```from this link: [https://vocf.wordpress.com/2008/02/18/using-tor-in-ubuntu-torify-our-life/](https://vocf.wordpress.com/2008/02/18/using-tor-in-ubuntu-torify-our-life/) Basically, I added these two lines to my /etc/privoxy/config:

```

listen-address 127.0.0.1:8118
forward-socks4a / localhost:9050 .
```but I keep getting this error message when I restart the TOR/privoxy server:
```

Sep 02 19:29:42.471 b780c8d0 Error: Ignoring unrecognized directive  'forward-socks:4a / localhost:9050 .' (314890724ul) in line 729 in  configuration file (/etc/privoxy/config)

```I assume the error is because the instructions are for *buntu 6.06, but I can't find any more recent instructions. Any help here? There must be some way of doing this in more recent versions of Ubuntu, right?

Thank you!

EDIT: I had a small error (based on the sample in the file) in /etc/privoxy/config: the forward-socks4a had a colon between socks and 4a which isn't in the sample in the file. However, now I don't get an error message when I restart; it just says fail in red. I tried using forward-socks4a, forward-socks5 but nothing works. Any ideas?

---

