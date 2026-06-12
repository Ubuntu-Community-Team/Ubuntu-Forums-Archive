---
title: "Set up system to act as a proxy"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by wesg on 2010-01-18
If my Ubuntu server were to act as a router/switch what have you, is it possible to set up a proxy to modify the IP address that websites view you as? Maybe I've completely misunderstood the idea of a proxy, but I think that being able to choose your location could be very useful (Hulu for those outside the US!).

---

### Post by Prospero2006 on 2010-01-18
That doesn't sound plausible because the packets have to know where they are bound for and returning to. They always come back to you.

Now, you could set yourself up to use a 3rd party proxy that is physically inside the US. Then, Hulu would only see the proxy address, but I don't think you can alter your perceived ip without a physical middle server somewhere else.

?

---

### Post by Lars Noodén on 2010-01-19
> **wesg said:**
> If my Ubuntu server were to act as a router/switch what have you, is it possible to set up a proxy to modify the IP address that websites view you as?

If you use the proxy, and it is set right, then your address will appear to be that of the proxy.  If you want the proxy to have a different address, then you have to move it there to that address.  

So if your proxy is in China, you look like you are in China.  If it is in Vietnam, you look like you are in Vietnam, if it is Australia you look like you are in Australia, and so on.

---

