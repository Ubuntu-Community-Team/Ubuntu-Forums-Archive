---
title: "Tor node problem"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by bitf on 2009-07-01
I started running a Tor node using Vidalia, it worked fine on the first day, but on the seconed day I got the message
[INDENT][FONT="Courier New"]Jul 01 19:03:51.972 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jul 01 19:03:51.972 [Notice] Closing partially-constructed listener OR listener on 0.0.0.0:9001
Jul 01 19:03:51.972 [Notice] Closing partially-constructed listener Directory listener on 0.0.0.0:9030
Jul 01 19:03:51.972 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jul 01 19:03:51.972 [Error] Reading config failed--see warnings above.
[/FONT][/INDENT]
A system monitor check confirmed was not running, so I figured it was the fact that had changed the torc files to make it firewall friendly, but when I reset it to what I believe was the original  configuration and the restarted the computer, the messages persisted.
Could it be that my IP has been reset at least once between use or is it something else?

---

### Post by Boondoklife on 2009-07-01
Can you post the output of `netstat -an | grep 127.0.0.1` and `netstat -pa | grep localhost`

---

### Post by bitf on 2009-07-01
> **maletek said:**
> Can you post the output of `netstat -an | grep 127.0.0.1` and `netstat -pa | grep localhost`
respectively:
tcp        0      0 127.0.0.1:631           0.0.0.0:*             LISTEN     
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN 

and:

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN      -               
tcp        0      0 localhost.localdom:9050 *:*                     LISTEN      -

---

### Post by Boondoklife on 2009-07-01
> **bitf said:**
> respectively:
tcp        0      0 127.0.0.1:631           0.0.0.0:*             LISTEN     
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN 

and:

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN      -               
tcp        0      0 localhost.localdom:9050 *:*                     LISTEN      -

put a sudo infront of the second command. It does indeed appear that tor is already running as you can see it on localhost and 127.0.0.1.

Are you not able to connect to it?

---

### Post by bitf on 2009-07-02
> **maletek said:**
> put a sudo infront of the second command. It does indeed appear that tor is already running as you can see it on localhost and 127.0.0.1.

Are you not able to connect to it?
Here it is (part of it)
tcp        0      0 localhost.localdom:9050 *:*                     LISTEN      3198/tor 
How do I stop it so I can control it through Vidalia?

---

### Post by bitf on 2009-07-03
bump

---

### Post by Boondoklife on 2009-07-03
Doesnt vidalia simply connect to the tor service? I know with windoes there is a way to tell it not to start tor so maybe there is an option in there you can change.

I dont use vidalia, I have tor installed on my NAS and just your firefox-torbutton to connect to it.

---

### Post by bitf on 2009-07-03
> **Boondoklife said:**
> Doesnt vidalia simply connect to the tor service? I know with windoes there is a way to tell it not to start tor so maybe there is an option in there you can change.

I dont use vidalia, I have tor installed on my NAS and just your firefox-torbutton to connect to it.
I tried telling Vidalia not to start Tor until I tell it to, but got the same error message when I started Tor

---

### Post by Boondoklife on 2009-07-03
Well only thing left I can think of would be to check the services that are started, System -> Admin -> Services If to r is there disable it.

---

### Post by bitf on 2009-07-03
> **Boondoklife said:**
> Well only thing left I can think of would be to check the services that are started, System -> Admin -> Services If to r is there disable it.

It's not there (Tor, not the services)

---

### Post by Boondoklife on 2009-07-03
try to kill it and then start vidalia
```
killall -9 tor
```

---

### Post by bitf on 2009-07-04
> **Boondoklife said:**
> try to kill it and then start vidalia
```
killall -9 tor
```

Did that, netstat confirmed that Tor was not running. But Vidalia wouldn't start Tor, the logs were:
Jul 04 16:21:38.419 [Warning] Error setting configured user: <myname> not found
Jul 04 16:21:38.419 [Warning] Failed to parse/validate config: Problem with User value. See logs for details.
Jul 04 16:21:38.419 [Error] Reading config failed--see warnings above.

---

### Post by Boondoklife on 2009-07-04
> **bitf said:**
> Did that, netstat confirmed that Tor was not running. But Vidalia wouldn't start Tor, the logs were:
Jul 04 16:21:38.419 [Warning] Error setting configured user: <myname> not found
Jul 04 16:21:38.419 [Warning] Failed to parse/validate config: Problem with User value. See logs for details.
Jul 04 16:21:38.419 [Error] Reading config failed--see warnings above.

Looks like your config is not setup right, check the log as it says and see what it says.

---

### Post by bitf on 2009-07-04
> **Boondoklife said:**
> Looks like your config is not setup right, check the log as it says and see what it says.
which log?

---

### Post by bitf on 2009-07-06
bump

---

### Post by bitf on 2009-07-09
bump

---

### Post by bitf on 2009-07-10
> **bitf said:**
> bump
bump

---

