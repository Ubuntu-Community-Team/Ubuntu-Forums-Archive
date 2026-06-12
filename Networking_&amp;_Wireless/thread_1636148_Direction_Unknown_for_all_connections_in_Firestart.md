---
title: "Direction Unknown for all connections in Firestarter"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by elusivespoon on 2010-12-02
I'm trying to setup a whitelist for outgoing connections with Firestarter (Outbound traffic policy: Restrictive by default). However all Blocked connections have a Direction of Unknown, though the source is always my computer. This seems to prevent the Events right-click menu from showing outbound options, and thus prevents me from allowing outbound connections to specific sites. Instead the context menu gives me options for inbound connections.

How can I get the Events right-click menu to give options for allowing connections to the destination, or to know the direction of traffic?

If you have a GUI whitelist solution other than Firestarter, that would be fine too.

Thanks.

---

### Post by cybergnome on 2010-12-02
Right clicking on Events, the menu item Show Column sets the information to be displayed in Events.  By default, In and Out are not checked.  That is for displaying events only, however.  You use Policy to set the rules for which you wish the firewall to function.

I haven't explored Firestarter, but it (should) allow for rule setting on the basis of incoming, outgoing, ports, addresses/ranges of addresses, packet protocol types, and perhaps applications.

You should also be aware that some of these functions may be available via the software in your router, as well.  Worth a look.

---

### Post by elusivespoon on 2010-12-02
The In and Out columns don't add any useful information. What I'm looking for is the "Allow Connections to Destination" described in the documentation for the [Events Page]("http://www.fs-security.com/docs/events-page.php"). Yes, I could just create rules for those things I want whitelisted by typing them out. But it would be much better if I could, say, attempt to go to a webpage, see that it is blocked in the events, then just right click it to allow it, rather than having to copy down the IP address and type it into a rule.

---

### Post by elusivespoon on 2010-12-02
Did a little digging and found the issue. In logread.c there is the following line:
```
h->direction = g_strstrip (get_text_between (line, "kernel:", "IN"));
```
that determines the direction based on what appears between "kernel:" and "IN". However kernel messages are of the form 
```
kernel: [  485.982878] Direction IN=
```
so it get's the number in brackets as well as the direction. I changed the line to match what's between "]" and "IN" and now it works as expected.

---

