---
title: "Serve files to a remote IP address"
date: 2010-02-22
forum: Multimedia Software
---

### Post by Neezer on 2010-02-22
Hi,

I am curious about someting and I'm not sure if it belongs here, or in networking. 

I have a media server with all my music and movies on it. Right now I have mediatomb on it serving up files to my ps3. They are on the same LAN. Is there a way to accomplish the same thing, but have them on different networks? Can I tell the ps3 to search an external IP addres on port 2222 to look for a media server?

If that won't work (I doubt it will), is there another way to do this? I am moving to Germany in 5 months for work and I Won't be able to bring my media server with me. I'm taking a bunch of stuff to my parent's to avoid rent and all....So I could just hook the server up to the router, set it to forward a port and have access to it.

---

### Post by alphacrucis2 on 2010-02-22
> **Neezer said:**
> Hi,

I am curious about someting and I'm not sure if it belongs here, or in networking. 

I have a media server with all my music and movies on it. Right now I have mediatomb on it serving up files to my ps3. They are on the same LAN. Is there a way to accomplish the same thing, but have them on different networks? Can I tell the ps3 to search an external IP addres on port 2222 to look for a media server?

If that won't work (I doubt it will), is there another way to do this? I am moving to Germany in 5 months for work and I Won't be able to bring my media server with me. I'm taking a bunch of stuff to my parent's to avoid rent and all....So I could just hook the server up to the router, set it to forward a port and have access to it.

The ps3 would need to connect to the public ip address of the router where your media server is located. You then configure port forwarding on the router to get to the internal private address. You may also want to configure some sort of access rule on the router so that the general public can't connect to your media server. A more secure way to do it would be to use something like OpenVPN but i don't know if there is an OpenVPN client for the ps3.

---

