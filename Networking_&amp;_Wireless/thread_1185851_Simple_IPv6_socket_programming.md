---
title: "Simple IPv6 socket programming"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by antonio_baez on 2009-06-12
Hello Guys!

I have a question about some IPv6 socket programming (in C). I'm in charged of doing some specific task in IPv6 and I'm getting my bearings in that field.

Since i'm new to this, I decided to start with some basic. I thought a good practice will be to use the gethostbyname2() function so given the host name of the PC it will return to you (using the hostent struct and so forth) the IPv6 address. But even something as simple as that, I have not been able to accomplished. 

When I compiled it using gcc it returns no errors, but when I run it, the printf function you will see (that is actually a dummy one, kind of making sure the program is getting there) can be seen but afterwards, it "thinks" for a couple of seconds, and then says "segmentation faults".

Here is the core of the code:
```

/*TESTING gethostbyname2();*/
        printf("I'm in\n");
        struct hostent *hp;
        struct in6_addr a;
        char *buf_addr;     //not using right now
        hp = gethostbyname2(HOST, AF_INET6);
        printf("Official name: %s\n\n",hp->h_name); //Seg.Faul occurs around here and I can't see the IPv6 address of my Ubuntu

```

HOST is declared as:
#define HOST "antonio-desktop" //which is the hostname of my ubuntu

It must be something with the gethostbyname2() since if I comment it, there is no segmentation faults. 

All libraries are included:
#include <stdio.h>
#include <sys/socket.h>	 //: socket(), connect(), send(), recv(),
#include <arpa/inet.h>	 //: htons(),
#include <string.h>	 //: memset(),
#include <sys/types.h>	 //: 
#include <netinet/in.h>

What I'm starting to think is that It must be something with the IPv6 setup? Im running Ubuntu 9.04, which I know that it has IPv6 features.

I really thank you for your time and effort.
Antonio.

---

### Post by lensman3 on 2009-06-12
Check if hp returned by gethostbyname2 is NULL.  Code in Handbreak implies that fqdn can return a null.

Should HOST be a 

char host[] = "hostname.xxx"  ?

You might have better luck moving this question to:

Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming

---

### Post by antonio_baez on 2009-06-13
Hi! Thanks for your response...

Yes indeed, I've checked if hp was a NULL pointer but it was not. Now, there is somehting funny...searching through the hp struct, I noticed this:

The value of the hp->h_length was 16 (which make sense in a IPv6 address) BUT...

If I check the size of the hp->h_addr_list it is 4 bytes....

Then, How come?

---

