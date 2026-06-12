---
title: "Ubuntu Network Connectivity"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by The_Shady_1 on 2010-05-02
I'm having some trouble connecting to the Internet under 10.04. I was connected when I last used it y-day but when I turned on today I have no connection. I've restarted it and nothing. I am however connected on the same machine under W7. In Ubuntu I couldn't even connect to my router (DIR-655) to see if there was an issue on the router. How do I fix this? :confused:

---

### Post by Iowan on 2010-05-02
Are you attempting wired or wireless connection?

---

### Post by The_Shady_1 on 2010-05-02
Wired connection.

---

### Post by Iowan on 2010-05-02
**ifconfig -a** shows no IP address?

---

### Post by The_Shady_1 on 2010-05-02
Dont see any IP in there other than 127.0.0.1

---

### Post by The_Shady_1 on 2010-05-04
When I'm in W7 I notice that the connection manager is a bit slow  pulling an IP off of my router. It will connect to the Internet but it just takes a second to do it. Wondering if these issues are related. Still have no Internet connectivity under Ubuntu. Anybody?:confused:

---

### Post by The_Shady_1 on 2010-05-04
I fixed it. All I did was right click on the Network Connection Manager and **un**checked enable networking then I just clicked enable networking.All is now well.

---

