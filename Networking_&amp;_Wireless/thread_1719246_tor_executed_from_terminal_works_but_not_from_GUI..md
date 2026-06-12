---
title: "tor executed from terminal works but not from GUI."
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by syoon on 2011-04-01
Hello, I have a strange problem, and I tried my best to figure it out by myself, but I can't at all. 

I am using Tor 0.2.1.30 with Polipo and Vidalia 0.1.15, Ubuntu 10.04.

Running tor on terminal works fine, but vidalia gets stuck at 85%
The message log, as I understand it, shows it getting stuck at finding the right bridges, but the terminal tor is able to connect fine...

##This is what the vidalia log looks like. The log shows me trying it two times. 

Apr 02 01:32:56.698 [Notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 02 01:32:56.699 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 02 01:32:56.699 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 02 01:32:56.699 [Notice] Opening Control listener on 127.0.0.1:9051
Apr 02 01:32:56.699 [Notice] Parsing GEOIP file.
Apr 02 01:53:08.204 [Notice] Have tried resolving or connecting to address '[scrubbed]' at 3 different places. Giving up.
Apr 02 01:58:25.732 [Notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 02 01:58:25.733 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 02 01:58:25.733 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 02 01:58:25.733 [Notice] Opening Control listener on 127.0.0.1:9051
Apr 02 01:58:25.733 [Notice] Parsing GEOIP file.
Apr 02 01:58:25.948 [Notice] OpenSSL OpenSSL 0.9.8k 25 Mar 2009 [9080bf] looks like it's older than 0.9.8l, but some vendors have backported 0.9.8l's renegotiation code to earlier versions, and some have backported the code from 0.9.8m or 0.9.8n.  I'll set both SSL3_FLAGS and SSL_OP just to be safe.
Apr 02 01:58:26.754 [Notice] new bridge descriptor 'charlternativi' (cached)
Apr 02 01:58:26.815 [Notice] Bootstrapped 5%: Connecting to directory server.
Apr 02 01:58:26.910 [Notice] We now have enough directory information to build circuits.
Apr 02 01:58:26.910 [Notice] Bootstrapped 80%: Connecting to the Tor network.
Apr 02 01:58:27.134 [Notice] Bootstrapped 85%: Finishing handshake with first hop.
...and then fail.


##This is what the tor (run from terminal) looks like.

Apr 02 01:34:17.672 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Apr 02 01:34:17.674 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 02 01:34:17.674 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 02 01:34:17.674 [notice] Opening Control listener on 127.0.0.1:9051
Apr 02 01:34:17.675 [notice] Parsing GEOIP file.
Apr 02 01:34:17.939 [notice] OpenSSL OpenSSL 0.9.8k 25 Mar 2009 [9080bf] looks like it's older than 0.9.8l, but some vendors have backported 0.9.8l's renegotiation code to earlier versions, and some have backported the code from 0.9.8m or 0.9.8n.  I'll set both SSL3_FLAGS and SSL_OP just to be safe.
Apr 02 01:34:18.695 [notice] We now have enough directory information to build circuits.
Apr 02 01:34:18.696 [notice] Bootstrapped 80%: Connecting to the Tor network.
Apr 02 01:34:18.967 [notice] Bootstrapped 85%: Finishing handshake with first hop.
Apr 02 01:34:20.539 [notice] Bootstrapped 90%: Establishing a Tor circuit.
Apr 02 01:34:23.154 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Apr 02 01:34:23.154 [notice] Bootstrapped 100%: Done.

I didn't include it, but the info level of the log for vidalia shows it failing with circuits at 85%. 

I don't think the problem is tor starting at system startup. I fixed it before this problem.  

I'm really curious as to why this is. Any help will be much appreciated!
Thank you.

---

### Post by syoon on 2011-04-03
OK. So this time I tried downloading the browser bundle and running that. I get this error. 


Apr 04 01:36:12.329 [Warning] X509_verify on cert and pkey returned <= 0
Apr 04 01:36:12.330 [Warning] TLS error while verifying certificate with [scrubbed]: block type is not 01 (in rsa routines:RSA_padding_check_PKCS1_type_1:SSL_ST_OK)
Apr 04 01:36:12.330 [Warning] TLS error while verifying certificate with [scrubbed]: padding check failed (in rsa routines:RSA_EAY_PUBLIC_DECRYPT:SSL_ST_OK)
Apr 04 01:36:12.330 [Warning] TLS error while verifying certificate with [scrubbed]: EVP lib (in asn1 encoding routines:ASN1_item_verify:SSL_ST_OK)
Apr 04 01:32:23.015 [Warning] Tried connecting to router at **.***.**.***:****: It has a cert but it's invalid. Closing.
Does anyone know what is going on?

---

