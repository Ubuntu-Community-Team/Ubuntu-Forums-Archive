---
title: "Browser code and webcam code"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by ky5u on 2010-10-05
Hi all,

I am needing help with two things:

Does anyone have sample 'c' code for a browser basic function, get an address and display the contents?  Want to learn bout how it's done.  

Second, can anyone point me to the source for "webcam", a webcam capture program?  I spent a day on the internet trying to find a home page or source listing. 

Sorry if these are "dumbassed" questions, but I am new back to Linux.  Been out of the Unix world since 1989.

Charlie

---

### Post by SeijiSensei on 2010-10-06
For the first question, you'd need to replicate the following sequence of events in your code:

```

$ telnet www.google.com 80
Trying 173.194.35.104...
Connected to www.l.google.com.
Escape character is '^]'.
GET / HTTP/1.1
Host: www.google.com
[Enter an empty new line]

```

You'll see the server respond with HTTP/1.1 OK then write the webpage to the screen.

The text-mode browser elinks and the command-line HTTP client wget are both open-sourced so you could study the code they use for help.

You can also study [RFC 2616](http://www.faqs.org/rfcs/rfc2616.html) where the HTTP protocol is described.

As for your second question, perhaps the source code for the application called Cheese might help.

---

### Post by ky5u on 2010-11-02
Thanks!  Exactly what I needed. You the man!

---

