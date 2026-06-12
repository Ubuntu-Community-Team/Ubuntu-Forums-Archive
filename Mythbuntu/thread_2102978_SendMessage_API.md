---
title: "SendMessage API"
date: 2013-01-08
forum: Mythbuntu
---

### Post by TheFuzz4 on 2013-01-08
Hey Everyone,

So I'm using PBXIAF at home with Asterisk and the CallerID Superfecta module.  The owner of that module just created a new plugin for it that will send the CallerID information to MythTV and I'm currently testing it.  It appears to be working to me however though when I test the API call with the address:  "http://192.168.1.139:6544/Myth/SendMessage?Message=%22Incoming+call+from+Test%3A%28303%29+777-3456%22"

In my browser I get the XML True response so the backend got the call and accepted but on all of my front ends nothing shows up.  I'm wondering is there something that I need to have turned on, on the front ends?  Thank you for your help.

---

### Post by tgm4883 on 2013-01-09
> **TheFuzz4 said:**
> Hey Everyone,

So I'm using PBXIAF at home with Asterisk and the CallerID Superfecta module.  The owner of that module just created a new plugin for it that will send the CallerID information to MythTV and I'm currently testing it.  It appears to be working to me however though when I test the API call with the address:  "http://192.168.1.139:6544/Myth/SendMessage?Message=%22Incoming+call+from+Test%3A%28303%29+777-3456%22"

In my browser I get the XML True response so the backend got the call and accepted but on all of my front ends nothing shows up.  I'm wondering is there something that I need to have turned on, on the front ends?  Thank you for your help.

The SendMessage command is one of the few frontend services (eg. You connect to the frontend to do it, not the backend). See [http://www.mythtv.org/wiki/Frontend_Service#SendMessage](http://www.mythtv.org/wiki/Frontend_Service#SendMessage)

---

### Post by TheFuzz4 on 2013-01-09
Thanks for the clarification on that.  If I wanted to send a broadcast message to all frontends do you have a suggestion on how that could be accomplished?  Thanks.

---

### Post by BicyclerBoy on 2013-01-09
To send mess to one frontend:
netcat -uv -q1 -w 0 mythhostname 6948 < message.txt

where message.txt
```

<mythmessage version="1">
  <text> Test Message Text</text>
  <timeout>5</timeout>
</mythmessage>

```

or can use "mythutil --message --message_text='Test Mess' --timeout=10 --bcastaddr hostIP" 

To send to all FE this might work:
set hostIP to 0.0.0.0
netcat can probably broadcast as well..

---

