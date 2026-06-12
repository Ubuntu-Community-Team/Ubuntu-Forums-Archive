---
title: "Can't connect with Remote Desktop Viewer since 12.04 upgrade."
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by squarethumps on 2013-03-27
I'm unable to connect to a remote machine using the Remote Desktop Viewer since I upgraded to 12.04 sometime last year.  ( I've been hacking away at this but no joy ) 

I have enabled Desktop Sharing on the remote machine and the firewall status allows port 5900 from Anywhere

I can ssh to that machine as well.

When I try to connect via Remote Desktop Viewer I get 

"Connection to host <ip address> was closed."

I will take all advice and suggestions that are offerred, but I'd like to explore two things if someone knows how to do this : 
1. What is the config file that defines which port the server and the client are using ?  ( I might have delved too deeply and changed this port and I just want to make sure it is 5900 ) 
2. I can't seem to find any way to get diagnostics on the Remote Desktop Viewer ( verbose ) to determine exactly what the error is beyond "was closed"

Many thanks for any and all assistance.

---

### Post by squarethumps on 2013-04-01
le bump  -- 

no one has experience here eh ?

---

### Post by ahallubuntu on 2013-04-01
~

---

### Post by squarethumps on 2013-04-01
I'm sorry, perhaps I didn't make it clear.   I'm not using MS Windows in any of this.   Both the client and the server are running ubuntu.

"Remote Desktop Viewer" is the name of the program ( both link and title bar ) that is run on the client machine.

So. yes, I'm using VNC.

---

### Post by steeldriver on 2013-04-01
In 12.04 afaik the vino-server config is all done via dconf - you can either install the dconf editor and navigate to desktop -> gnome -> remote access, or use dconf command line to query the value

```
dconf read /desktop/gnome/remote-access/alternative-port
```

(confusingly it only seems to return a value if the setting is not the default); or possibly use gsettings with the schema 'org.gnome.Vino' e.g.

```
$ gsettings list-recursively org.gnome.Vino
org.gnome.Vino alternative-port uint16 5900
org.gnome.Vino authentication-methods ['vnc']
org.gnome.Vino disable-background false
org.gnome.Vino disable-xdamage false
org.gnome.Vino enabled true
org.gnome.Vino icon-visibility 'client'
org.gnome.Vino lock-screen-on-disconnect true
org.gnome.Vino mailto ''
org.gnome.Vino network-interface 'lo'
org.gnome.Vino notify-on-connect true
org.gnome.Vino prompt-enabled false
org.gnome.Vino require-encryption false
org.gnome.Vino use-alternative-port false
org.gnome.Vino use-upnp false
org.gnome.Vino view-only false
org.gnome.Vino vnc-password 'VGhlTWlC'

```

which should list ALL the key-value pairs (default and non-default). Alternatively you could run netstat to see what port (if any) the server is listening on

```
$ sudo netstat -nlp | grep vino
```

The client config should all be visible in the remmina connection properties dialog

---

### Post by squarethumps on 2013-04-01
Thanks for the response.

It looks like the default port is set which is good : 
```
root@argonaut:~# dconf read /desktop/gnome/remote-access/alternative-port
root@argonaut:~# 

```

I believe that this further confirms that 5900 is the port being used : 

```
root@argonaut:~# gsettings list-recursively org.gnome.Vino
org.gnome.Vino alternative-port uint16 5900
org.gnome.Vino authentication-methods ['none']
org.gnome.Vino disable-background false
org.gnome.Vino disable-xdamage false
org.gnome.Vino enabled false
org.gnome.Vino icon-visibility 'client'
org.gnome.Vino lock-screen-on-disconnect false
org.gnome.Vino mailto ''
org.gnome.Vino network-interface ''
org.gnome.Vino notify-on-connect true
org.gnome.Vino prompt-enabled true
org.gnome.Vino require-encryption false
org.gnome.Vino use-alternative-port false
org.gnome.Vino use-upnp false
org.gnome.Vino view-only false
org.gnome.Vino vnc-password 'keyring'

```



This coule be the problem : 

```
root@argonaut:~#  netstat -nlp  | grep -i vino
root@argonaut:~#
 root@argonaut:~# ps -ef | grep -i vino
root     10734 10489  0 17:51 pts/7    00:00:00 grep -i vino
root@argonaut:~# 


```

vino doesn't appear to be running, even though I've gone through the gui steps to enable desktop sharing.

Any ideas what would be preventing this or how I might go about diagnosing why it wouldn't actually run ? error file or some verbose output ?  I'll be googling as well in the meantime .. 

Many Thanks for the responses  !

---

### Post by steeldriver on 2013-04-01
Hmm I don't really know - have you tried turning it off and back on again lol (unchecking and checking the 'allow' box in Desktop Sharing)? notice that your gsettings output does say 'enabled false' ...

Other than that, you could see if there are any relevant xsession-errors

```
grep -i vino ~/.xsession-errors
```

---

### Post by squarethumps on 2013-04-01
Ok .. I don't really understand but --- 

"vino-server" was not available as a regular binary.   It was in /usr/lib/vino/vino-server

I was able to run this as a non-root user, and I was then able to connect to this machine from another ubuntu machine with the Remote Desktop Viewer.

```

user@argonaut:~$ /usr/lib/vino/vino-server &

(vino-server:10815): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
01/04/2013 06:00:07 PM Autoprobing TCP port in (all) network interface
01/04/2013 06:00:07 PM Listening IPv6://[::]:5900
01/04/2013 06:00:07 PM Listening IPv4://0.0.0.0:5900
01/04/2013 06:00:07 PM Autoprobing selected port 5900
01/04/2013 06:00:07 PM Advertising security type: 'TLS' (18)
01/04/2013 06:00:07 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
01/04/2013 06:00:07 PM Listening IPv6://[::]:5900
01/04/2013 06:00:07 PM Listening IPv4://0.0.0.0:5900
01/04/2013 06:00:07 PM Clearing securityTypes
01/04/2013 06:00:07 PM Advertising security type: 'TLS' (18)
01/04/2013 06:00:07 PM Clearing securityTypes
01/04/2013 06:00:07 PM Advertising security type: 'TLS' (18)
01/04/2013 06:00:07 PM Advertising authentication type: 'No Authentication' (1)
01/04/2013 06:00:07 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
01/04/2013 06:00:07 PM Listening IPv6://[::]:5900
01/04/2013 06:00:07 PM Listening IPv4://0.0.0.0:5900
01/04/2013 06:00:07 PM Listening for VNC connections on TCP port 5900 in (all) network interface
01/04/2013 06:00:07 PM Listening IPv6://[::]:5900
01/04/2013 06:00:07 PM Listening IPv4://0.0.0.0:5900
01/04/2013 06:00:07 PM Clearing securityTypes
01/04/2013 06:00:07 PM Clearing authTypes
01/04/2013 06:00:07 PM Advertising security type: 'TLS' (18)
01/04/2013 06:00:07 PM Advertising authentication type: 'VNC Authentication' (2)
01/04/2013 06:00:07 PM Clearing securityTypes
01/04/2013 06:00:07 PM Clearing authTypes
01/04/2013 06:00:07 PM Advertising security type: 'TLS' (18)
01/04/2013 06:00:07 PM Advertising authentication type: 'VNC Authentication' (2)
01/04/2013 06:00:07 PM Advertising security type: 'VNC Authentication' (2)

(vino-server:10815): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(vino-server:10815): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.



```


Any ideas why vino-server didn't run when I enabled it through the GUI preferences ? ( vino-preferences )

---

### Post by squarethumps on 2013-04-01
Yes, I now see that "enabled" is false. ( however, I must have been playing with it and had the box unchecked at that moment )

When I turn it on and get the settings output it does say "true", and when I click the box in vino-preferences again to sut it off, and then run the settings output, it says false.  Though I do notice now that it is saying "use alternate port is true" .. which it was false before .. 

```
user@argonaut:~$ gsettings list-recursively org.gnome.Vino
org.gnome.Vino alternative-port uint16 5900
org.gnome.Vino authentication-methods ['vnc']
org.gnome.Vino disable-background false
org.gnome.Vino disable-xdamage false
org.gnome.Vino enabled true
org.gnome.Vino icon-visibility 'client'
org.gnome.Vino lock-screen-on-disconnect false
org.gnome.Vino mailto ''
org.gnome.Vino network-interface ''
org.gnome.Vino notify-on-connect true
org.gnome.Vino prompt-enabled false
org.gnome.Vino require-encryption false
**org.gnome.Vino use-alternative-port true**
org.gnome.Vino use-upnp true
org.gnome.Vino view-only false


```


Yes, I have tried turning it on and off again many times.

It seems like since I ran it with the command line the **use-alternative-port **is now true .. 

And once I have the server running I have to leave that terminal open or the process ends .. ( which I would expect ) ...

---

### Post by steeldriver on 2013-04-01
that's the normal place for the binary I think - this is what I see when enabled from the 'Destop Sharing' app

```
$ ps -ef | grep vino
steeldriver 18401 18324 14 16:35 ?        00:14:18 /usr/lib/vino/vino-server --sm-disable
steeldriver 20765 18594  0 18:15 pts/1    00:00:00 grep --color=auto vino
```

I guess if you don't mind other default settings you could try resetting everything in the schema

```
gsettings reset-recursively org.gnome.Vino
```

---

### Post by squarethumps on 2013-04-01
> that's the normal place for the binary I think -

For some reason I can usually "tab complete" binarys.  This one I can't .. the only ones that are returned when I type "vino" and hit "Tab" are :

```

root@argonaut:~# vino-p
vino-passwd       vino-preferences  

```

so I would have thought that it would have given me the vino-server result as well ... 

> I guess if you don't mind other default settings you could try resetting everything in the schema

I'm not sure of the all the settings that I've set ..  I'm on the box 8 hrs a day at work.  I may end up resetting them tomorrow and seeing what happens.

For now my solution will be just to run it manually.  I am able to ssh to the machine so it seems that I will always be able to start it.

Thank you very much for the help and assistance.

---

