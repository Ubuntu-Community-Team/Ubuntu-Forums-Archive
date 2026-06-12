---
title: "FreeRadius connectivity problems"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by FreeradiusVictim on 2012-11-26
Hi,

We have just recently installed and configured a Freeradius service on this Ubuntu machine. We plan to use Freeradius to authenticate users via mac address and 802.1 x EAP.

Problem is that while the Freeradius gives a "Auth-Type = Accept" after passing all tests, the user can't connect to the internet and is booted from the network that uses Freeradius auth in less than a minute. 

There is no message in Freeradius debug mode when this happens, so I'm a bit lost here.

Another thing worth of note is that we are using a Ruckus ZoneDirector to manage our networks, and there is a Authentication Test in it, used to check if everything works ok. The problem here is that it gives a FAILED result with the settings that give Auth-Type = Accept, but if I go and remove all the auth checks in the sites-enabled/default config file, it gives a SUCCESS. So there is definetly something wrong with my configs.

I've been following the plain mac-auth guide to accomplish whatever I have now, but it still needs some tinkering. Problem is that I have no idea where to start.

Here is a log of what happens when a user connects to the freeradius guarded network:

```
 Ready to process requests.
rad_recv: Access-Request packet from host 192.168.154.12 port 1065, id=9, length=168
    User-Name = "60d819a89668"
    User-Password = "60d819a89668"
    Calling-Station-Id = "60-D8-19-A8-96-68"
    NAS-IP-Address = 192.168.154.12
    Called-Station-Id = "C4-01-7C-1A-50-69:opetusx"
    Service-Type = Framed-User
    NAS-Port-Type = Wireless-802.11
    NAS-Identifier = "C4-01-7C-1A-50-69"
    Vendor-25053-Attr-3 = 0x6f706574757378
    Message-Authenticator = 0xa7676bfa2ace5b4ba05356c35cac255a
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+- entering group authorize {...}
++[preprocess] returns ok
[authorized_macs]     expand: %{Calling-Station-ID} -> 60-D8-19-A8-96-68
[authorized_macs] users: Matched entry 60-D8-19-A8-96-68 at line 2
++[authorized_macs] returns ok
++? if (!ok)
? Evaluating !(ok) -> FALSE
++? if (!ok) -> FALSE
++- entering else else {...}
+++? if (!EAP-message)
? Evaluating !(EAP-message) -> TRUE
+++? if (!EAP-message) -> TRUE
+++- entering if (!EAP-message) {...}
++++[control] returns ok
+++- if (!EAP-message) returns ok
++- else else returns ok
++[chap] returns noop
++[mschap] returns noop
++[digest] returns noop
[suffix] No '@' in User-Name = "60d819a89668", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] No EAP-Message, not doing EAP
++[eap] returns noop
++[files] returns noop
++[expiration] returns noop
++[logintime] returns noop
[pap] WARNING: Auth-Type already set.  Not setting to PAP
++[pap] returns noop
Found Auth-Type = Accept
Auth-Type = Accept, accepting the user
# Executing section post-auth from file /etc/freeradius/sites-enabled/default
+- entering group post-auth {...}
++[exec] returns noop
Sending Access-Accept of id 9 to 192.168.154.12 port 1065
Finished request 0.
Going to the next request
Waking up in 4.9 seconds.
Cleaning up request 0 ID 9 with timestamp +7
Ready to process requests.

```


The contents of sites-enabled/default authorize portion are as follows:

```
authorize {
        #
        #  The preprocess module takes care of sanitizing some bizarre
        #  attributes in the request, and turning them into attributes
        #  which are more standard.
        #
        #  It takes care of processing the 'raddb/hints' and the
        #  'raddb/huntgroups' files.
        preprocess

        authorized_macs
        if (!ok) {
        reject
        }
        else {
        if (!EAP-message) {
        update control {
        Auth-Type := Accept
        }
        }
        }
        #else {
        #eap
        #}

```

Now this current thing is my own crude work, but I also used the examples given in plain mac auth wiki prior to this one, but they gave the same results.

Any ideas what I'm doing wrong here?

---

### Post by FreeradiusVictim on 2012-11-26
Also, we are using PAP on the Ruckus controller, the other option being CHAP. Switching between these two though seems to have no effect whatsoever.

I'm really at my wits end here.

---

### Post by FreeradiusVictim on 2012-11-30
Here is the freeradius debug feedback when I test a user with ruckus zone controller.

```
rad_recv: Access-Request packet from host 192.168.154.12 port 1064, id=7, length=81
    User-Name = "moi"
    User-Password = "moi"
    NAS-IP-Address = 192.168.154.12
    Service-Type = Login-User
    NAS-Port-Type = Wireless-802.11
    Message-Authenticator = 0xd26ed78e18d019ae6bf8a705f9429d86
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+- entering group authorize {...}
++[preprocess] returns ok
[authorized_macs]     expand: %{Calling-Station-ID} -> 
++[authorized_macs] returns noop
++? if (!ok)
? Evaluating !(ok) -> TRUE
++? if (!ok) -> TRUE
++- entering if (!ok) {...}
+++[reject] returns reject
++- if (!ok) returns reject
Using Post-Auth-Type Reject
# Executing group from file /etc/freeradius/sites-enabled/default
+- entering group REJECT {...}
[attr_filter.access_reject]     expand: %{User-Name} -> moi
 attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 9 for 1 seconds
Going to the next request
Waking up in 0.9 seconds.
Sending delayed reject for request 9
Sending Access-Reject of id 7 to 192.168.154.12 port 1064
Waking up in 4.9 seconds.
Cleaning up request 9 ID 7 with timestamp +346904
Ready to process requests.

```

---

