---
title: "pon dsl -provider shows error"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by debd on 2011-02-04
I configured my pppoe connection using

> sudo pppoeconf

I am well able to connect to the internet using this method.
But once disconnected, when I try

> pon dsl -provider

to connct again

it gives an error:

> Error: only members of the 'dip' group can use this command.

what is wrong?
what should I do?

---

### Post by dineshs on 2011-02-05
Try ```
sudo pon dsl-provider
```
or run 
```
sudo adduser username dip
sudo adduser username dialout

```[COLOR="Red"]substitute your username[/COLOR]
BTW why dont you try the DSL tab in NM
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

### Post by debd on 2011-02-05
ok..

I did what you said.
now the "members of dip group can use..." error doesn't show anymore. but when I try 

pon dsl -provider

the output is:


> debd@ubuntu:~$ pon -dsl provider
Usage: pon [OPTIONS] [provider] [arguments]
  -q|--quick           pppd hangs up after all ip-up scripts are run

If pon is invoked without arguments, /etc/ppp/ppp_on_boot file will be
run, presuming it exists and is executable. Otherwise, a PPP connection
will be started using settings from /etc/ppp/peers/provider.
If you specify one argument, a PPP connection will be started using
settings from the appropriate file in the /etc/ppp/peers/ directory, and
any additional arguments supplied will be passed as extra arguments to
pppd.

and when trying

> sudo pon -dsl provider

it gives out:
 sudo pon dsl provider
[sudo] password for debd: 
The file /etc/ppp/peers/dsl does not exist. Please create it or use
a command line argument to use another file in the /etc/ppp/peers/ directory.


but the thing is when configuring through  

sudo pppoeconf ;

it says the conf file that will hold the conn. settings is

/etc/ppp/peers/dsl-provider

what argument should I use to invoke the pppoe connection from this file?

---

### Post by dineshs on 2011-02-05
The command is ```
sudo pon dsl-provider
```and not > debd@ubuntu:~$ [COLOR="Red"]pon -dsl provider[/COLOR]I mean it is a typo

---

### Post by debd on 2011-02-05
thanks man...its right. worked.

thanks a lot.

I never realised. :)

---

