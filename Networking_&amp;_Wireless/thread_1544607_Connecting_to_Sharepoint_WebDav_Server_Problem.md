---
title: "Connecting to Sharepoint WebDav Server Problem"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by cd1zz on 2010-08-02
I am trying to connect to a Sharepoint server via WebDav using Nautilus. The Sharepoint box is a MS 2008 Server running MOSS server.

When I go to Places -> Connect to Server -> webdav I enter the following:

server - the ip address
folder - the webdav folder

I get an HTTP error that I am unauthorized. 

I suspect it is that I am trying to enter my AD credentials which are in the format DOMAIN\username. I think the \ is what is screwing it up. Is there an escape character to try? Am I doing this completely wrong?

Thanks in advance,
C

---

