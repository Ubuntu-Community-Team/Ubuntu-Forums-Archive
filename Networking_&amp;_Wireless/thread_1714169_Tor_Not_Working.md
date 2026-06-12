---
title: "Tor Not Working"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by pi.theta on 2011-03-25
Hi
I am trying to use tor (v2.1) behind an http proxy. I have kernel 2.6.37 installed. A few months back I was able to access the net through, but now I can't.
The notices log is as follows:
```
Mar 25 10:03:34.190 [notice] Tor 0.2.1.29 (r8e9b25e6c7a2e70c) opening log file.
Mar 25 10:03:34.239 [notice] Parsing GEOIP file.
Mar 25 10:03:34.468 [warn] You are running Tor as root. You don't need to, and you probably shouldn't.
Mar 25 10:03:34.576 [notice] OpenSSL OpenSSL 1.0.0d 8 Feb 2011 looks like version 0.9.8m or later; I will try SSL_OP to enable renegotiation
Mar 25 10:03:34.684 [notice] No current certificate known for authority moria1; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority tor26; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority dizum; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority ides; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority gabelmoo; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority dannenberg; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority urras; launching request.
Mar 25 10:03:34.684 [notice] No current certificate known for authority maatuska; launching request.
Mar 25 10:03:34.684 [notice] Bootstrapped 5%: Connecting to directory server.
Mar 25 10:03:34.741 [notice] I learned some more directory information, but not enough to build a circuit: We have no network-status consensus.
Mar 25 10:03:34.752 [notice] Bootstrapped 10%: Finishing handshake with directory server.
Mar 25 10:03:34.754 [notice] No current certificate known for authority moria1; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority tor26; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority dizum; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority ides; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority gabelmoo; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority dannenberg; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority urras; launching request.
Mar 25 10:03:34.754 [notice] No current certificate known for authority maatuska; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority moria1; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority tor26; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority dizum; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority ides; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority gabelmoo; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority dannenberg; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority urras; launching request.
Mar 25 10:04:35.822 [notice] No current certificate known for authority maatuska; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority moria1; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority tor26; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority dizum; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority ides; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority gabelmoo; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority dannenberg; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority urras; launching request.
Mar 25 10:09:40.142 [notice] No current certificate known for authority maatuska; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority moria1; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority tor26; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority dizum; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority ides; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority gabelmoo; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority dannenberg; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority urras; launching request.
Mar 25 10:19:50.784 [notice] No current certificate known for authority maatuska; launching request.
Mar 25 10:50:20.787 [notice] No current certificate known for authority moria1; launching request.
Mar 25 10:50:20.787 [notice] No current certificate known for authority tor26; launching request.
Mar 25 10:50:20.787 [notice] No current certificate known for authority dizum; launching request.
Mar 25 10:50:20.787 [notice] No current certificate known for authority ides; launching request.
Mar 25 10:50:20.787 [notice] No current certificate known for authority gabelmoo; launching request.
Mar 25 10:50:20.787 [notice] No current certificate known for authority dannenberg; launching request.
Mar 25 10:50:20.788 [notice] No current certificate known for authority urras; launching request.
Mar 25 10:50:20.788 [notice] No current certificate known for authority maatuska; launching request.

```

And the torrc file is:
```

    ## CONFIGURED FOR ARCHLINUX

    ## Last updated 22 July 2005 for Tor 0.1.0.13.
    ## (May or may not work for older or newer versions of Tor.)
    #
    ## See the man page, or http://tor.eff.org/tor-manual.html, for more
    ## options you can use in this file.
    #
    # On Unix, Tor will look for this file in someplace like "~/.tor/torrc" or
    # "/etc/torrc"
    #
    # On Windows, Tor will look for the configuration file in someplace like
    # "Application Data\tor\torrc" or "Application Data\<username>\tor\torrc"
    #
    # With the default Mac OS X installer, Tor will look in ~/.tor/torrc or
    # /Library/Tor/torrc

    ## Replace this with "SocksPort 0" if you plan to run Tor only as a
    ## server, and not make any local application connections yourself.
    SocksPort 9050 # what port to open for local application connections
    SocksBindAddress 127.0.0.1 # accept connections only from localhost
    #SocksBindAddress 192.168.0.1:9100 # listen on a chosen IP/port too

    ## Entry policies to allow/deny SOCKS requests based on IP address.
    ## First entry that matches wins. If no SocksPolicy is set, we accept
    ## all (and only) requests from SocksBindAddress.
    #SocksPolicy accept 192.168.0.1/16
    #SocksPolicy reject *

    ## Allow no-name routers (ones that the dirserver operators don't
    ## know anything about) in only these positions in your circuits.
    ## Other choices (not advised) are entry,exit,introduction.
    AllowUnverifiedNodes middle,rendezvous

    ## Logs go to stdout at level "notice" unless redirected by something
    ## else, like one of the below lines. You can have as many log lines as
    ## you want.
    ##
    ## Send all messages of level 'notice' or higher to /var/log/tor/notices.log
    Log notice file /var/log/tor/notices.log
    ## Send only debug and info messages to /var/log/tor/debug.log
    #Log debug-info file /var/log/tor/debug.log
    ## Send ONLY debug messages to /var/log/tor/debug.log
    #Log debug-debug file /var/log/tor/debug.log
    ## To use the system log instead of Tor's logfiles, uncomment these lines:
    Log notice syslog
    ## To send all messages to stderr:
    #Log debug stderr

    ## Uncomment this to start the process in the background... or use
    ## --runasdaemon 1 on the command line.
    RunAsDaemon 1
    #User tor
    #Group tor

    ## Tor only trusts directories signed with one of these keys, and
    ## uses the given addresses to connect to the trusted directory
    ## servers. If no DirServer lines are specified, Tor uses the built-in
    ## defaults (moria1, moria2, tor26), so you can leave this alone unless
    ## you need to change it.
    #DirServer 18.244.0.188:9031 FFCB 46DB 1339 DA84 674C 70D7 CB58 6434 C437 0441
    #DirServer 18.244.0.114:80 719B E45D E224 B607 C537 07D0 E214 3E2D 423E 74CF
    #DirServer 86.59.21.38:80 847B 1F85 0344 D787 6491 A548 92F9 0493 4E4E B85D

    ## The directory for keeping all the keys/etc. By default, we store
    ## things in $HOME/.tor on Unix, and in Application Data\tor on Windows.
    DataDirectory /var/lib/tor

    ## The port on which Tor will listen for local connections from Tor controller
    ## applications, as documented in control-spec.txt.  NB: this feature is
    ## currently experimental.
    #ControlPort 9051

    ############### This section is just for location-hidden services ###

    ## Look in .../hidden_service/hostname for the address to tell people.
    ## HiddenServicePort x y:z says to redirect a port x request from the
    ## client to y:z.

    #HiddenServiceDir /var/lib/tor/hidden_service/
    #HiddenServicePort 80 127.0.0.1:80

    #HiddenServiceDir /var/lib/tor/other_hidden_service/
    #HiddenServicePort 80 127.0.0.1:80
    #HiddenServicePort 22 127.0.0.1:22
    #HiddenServiceNodes moria1,moria2
    #HiddenServiceExcludeNodes bad,otherbad

    ################ This section is just for servers #####################

    ## NOTE: If you enable these, you should consider mailing your identity
    ## key fingerprint to the tor-ops, so we can add you to the list of
    ## servers that clients will trust. See
    ## http://tor.eff.org/doc/tor-doc.html#server for details.

    ## Required: A unique handle for this server
    #Nickname ididnteditheconfig

    ## The IP or fqdn for this server. Leave commented out and Tor will guess.
    #Address noname.example.com

    ## Contact info that will be published in the directory, so we can
    ## contact you if you need to upgrade or if something goes wrong.
    ## This is optional but recommended.
    #ContactInfo Random Person <nobody AT example dot com>
    ## You might also include your PGP or GPG fingerprint if you have one:
    #ContactInfo 1234D/FFFFFFFF Random Person <nobody AT example dot com>

    ## Required: what port to advertise for tor connections
    #ORPort 9001
    ## If you want to listen on a port other than the one advertised
    ## in ORPort (e.g. to advertise 443 but bind to 9090), uncomment
    ## the line below. You'll need to do ipchains or other port forwarding
    ## yourself to make this work.
    #ORBindAddress 0.0.0.0:9090

    ## Uncomment this to mirror the directory for others (please do)
    #DirPort 9030 # what port to advertise for directory connections
    ## If you want to listen on a port other than the one advertised
    ## in DirPort (e.g. to advertise 80 but bind 9091), uncomment the line
    ## below. You'll need to do ipchains or other port forwarding yourself
    ## to make this work.
    #DirBindAddress 0.0.0.0:9091

    ## A comma-separated list of exit policies. They're considered first
    ## to last, and the first match wins. If you want to *replace*
    ## the default exit policy, end this with either a reject *:* or an
    ## accept *:*. Otherwise, you're *augmenting* (prepending to) the
    ## default exit policy. Leave commented to just use the default, which is
    ## available in the man page or at http://tor.eff.org/documentation.html
    ##
    ## Look at http://tor.eff.org/faq-abuse.html#TypicalAbuses
    ## for issues you might encounter if you use the default exit policy.
    ##
    ## If certain IPs and ports are blocked externally, e.g. by your firewall,
    ## you should update your exit policy to reflect this -- otherwise Tor
    ## users will be told that those destinations are down.
    ##
    #ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
    #ExitPolicy accept *:119 # accept nntp as well as default exit policy
    #ExitPolicy reject *:* # middleman only -- no exits allowed
    HTTPProxy proxy_address:80
    HTTPProxyAuthenticator user:pass
    HTTPSProxy proxy_address:443
    HTTPSProxyAuthenticator user:pass
    #FascistFirewall 1
    ReachableAddresses *:80
    ReachableORAddresses *:443
```

---

### Post by pi.theta on 2011-03-28
Ok, the solution was slightly weird.
I had to expicitly specify

```
    ReachableAddresses reject *:*
```

in the tor configuration file.
I suppose that this was required becasue of the http proxy.

---

