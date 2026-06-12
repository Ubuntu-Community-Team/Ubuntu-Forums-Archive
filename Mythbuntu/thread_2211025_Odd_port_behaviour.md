---
title: "Odd port behaviour"
date: 2014-03-13
forum: Mythbuntu
---

### Post by jim.hitch on 2014-03-13
I've just rebuilt my server and restored the 0.25 database. I have some issues still, but one I'm struggling with is the port number.

Where can I definitively find out what it should be.

In general settings on the backend it's 6543, but I suspect this is from the database restore, so I changed it to 3306 as that's what's in mysql.txt (is that right?). However, mythwelcome is only working if the port is 6543. The frontend on the same machine seems happy with 3306 in its settings whatever the backend is set to, though my separate front end is not connecting at all if the port in its settings (XBMC frontend) are 6543, and seems to be happier (though not fixed yet) with 3306. 

Really am quite lost. I'd rather get a third port number and set everything to that. Is that possible?

Many thanks.

---

### Post by steeldriver on 2014-03-13
They're two different things I think - the way I understand it:

[LIST]
[*]the mythtv front end(s) connect to the mythbackend service on 6543 
[*]the mythbackend process connects to the mysql database on the standard mysql port 3306 
[/LIST]

---

### Post by jim.hitch on 2014-03-14
> **steeldriver said:**
> They're two different things I think - the way I understand it:

[LIST]
[*]the mythtv front end(s) connect to the mythbackend service on 6543 
[*]the mythbackend process connects to the mysql database on the standard mysql port 3306 
[/LIST]

Thanks for getting back to me. OK, got that, makes some sense to me.

In the backend, therefore, does the port number box under the general settings refer to 

a) the backend connecting to the database, or
b) the backend connecting to the frontend?

Surely it'd be better just to have them all using the same port? I'll investigate how to do that.... any easy answers very welcome!

---

### Post by steeldriver on 2014-03-14
The port in the mythbackend setup General page is the mythbackend port (6543). IIRC it also uses 6544 for status.

You can't have different *services *(mythbackend and mysqld) listening on the same port.

---

### Post by jim.hitch on 2014-03-14
OK. Before I attempted this rebuild of the backend everything in any GUI was set to 6543 (except for the 6544 you mentioned above), and everything worked like a dream for 3 years, but now I have a mixture of 6543 & 3306, that's why I'm confused. Possibly it's a difference between 0.23 & 0.25 MythTV?

---

