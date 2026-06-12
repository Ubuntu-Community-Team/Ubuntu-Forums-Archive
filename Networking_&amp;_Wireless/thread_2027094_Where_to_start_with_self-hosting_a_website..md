---
title: "Where to start with self-hosting a website."
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by MG&amp;TL on 2012-07-16
Hello network-ers. ):P

So, after quite a learning curve, I made a website for my mum. It's currently hosted locally on a headless server in my house. I'd really like it to be available to the internet as a whole, and I'm thinking about registering a [.tk]("http://dot.tk") domain name. It won't be a high-traffic site, and there's no user input involved, so as far as I'm concerned, it should be secure.

However, I've got BT as an ISP, and my understanding is that they use dynamic DNS, which is not very helpful. There's lots of tutorials about how to set this up on the web, but they all seem to have different situations/solutions.

So I was hoping that someone here could point me in the right direction. I can port-forward from my router, but I have a feeling that won't be enough. Right?

Why self-host? She wants a website, but doesn't want to pay anything. Fun. :lol:

---

### Post by Grenage on 2012-07-16
While you could use a dynamic IP address, it's not ideal.

Regarding cost, I'd still recommend getting a cheap hosted solution.  Sure it costs a few quid, but it may well (likely) be cheaper than the lecky you use keeping a home server ticking over.  It'll also be more reliable.

---

### Post by MG&amp;TL on 2012-07-16
> **Grenage said:**
> While you could use a dynamic IP address, it's not ideal.

Regarding cost, I'd still recommend getting a cheap hosted solution.  Sure it costs a few quid, but it may well (likely) be cheaper than the lecky you use keeping a home server ticking over.  It'll also be more reliable.

That's what I said. But, as always, "Parents know best". The lecky isn't too bad, it's a laptop. Seems to almost sleep when not serving pages as well.

How could I use a dynamic IP then?

---

### Post by Grenage on 2012-07-16
Don't they always?

You'll want to use something like DynDNS, and have your domain forward to that.  You may well be able to register a domain through such services, which will simplify the process.

---

### Post by MG&amp;TL on 2012-07-16
> **Grenage said:**
> Don't they always?

You'll want to use something like DynDNS, and have your domain forward to that.  You may well be able to register a domain through such services, which will simplify the process.

Ah, thanks grenage. I shall look into that then. So I can get a permament IP from DyDNS, then put the domain name onto that?

---

### Post by Grenage on 2012-07-16
Well you install a client on the server, which updates DynDNS with your dynamic IP; most home routers have an in-built section for this task, meaning you don't even need the software.

Your IP is still dynamic, but with your website forwarding to the DynDNS address (which is updates as it changes), the traffic should get through.  It's not pretty, but it should work.

I know that I mentioned it before, but you can get a year's hosting and a UK domain from as little as £15-18 per year.  It's a much more elegant solution; try and convince your mum! ;)

---

### Post by MG&amp;TL on 2012-07-16
> **Grenage said:**
> Well you install a client on the server, which updates DynDNS with your dynamic IP; most home routers have an in-built section for this task, meaning you don't even need the software.

Your IP is still dynamic, but with your website forwarding to the DynDNS address (which is updates as it changes), the traffic should get through.  It's not pretty, but it should work.

I know that I mentioned it before, but you can get a year's hosting and a UK domain from as little as £15-18 per year.  It's a much more elegant solution; try and convince your mum! ;)

I'll go with the DyDNS route for now; but I appreciate what you're saying (this seems somewhat painful for a simple task) and will try. Very hard. :)

---

### Post by MG&amp;TL on 2012-07-16
Thanks Grenage. :)

[Website]("http://alisonrawson.tk")

Not as hard as it looks, although every time my router goes down...oh well.

Thanks for your time.

---

### Post by Grenage on 2012-07-16
Excellent, good job; there are some stunning pictures in the gallery section. :)

---

### Post by prshah on 2012-07-16
> **MG&TL said:**
> Why self-host? She wants a website, but doesn't want to pay anything. Fun. :lol:

I suggest you look at AWS (Amazon Web Services). It's free for a micro instance (which is probably all that is required) for 1 year, and pretty much dirt cheap thereafter.

I suggest you use it for a while, and decide wether or not to continue with it within a year.

Remember, you "self-hosted" is not exactly free; you're paying for traffic and electricity, if nothing else. Security can be a right problem too.

---

### Post by MG&amp;TL on 2012-07-16
> **prshah said:**
> I suggest you look at AWS (Amazon Web Services). It's free for a micro instance (which is probably all that is required) for 1 year, and pretty much dirt cheap thereafter.

I suggest you use it for a while, and decide wether or not to continue with it within a year.

Remember, you "self-hosted" is not exactly free; you're paying for traffic and electricity, if nothing else. Security can be a right problem too.

Thanks for the hint. I shall look into it as soon as I can persuade her otherwise.

Why security? All that's running is Apache and PHP. On static pages. I'm not an expert, but I personally can't find any ways in. Feel free to test, you know where to find me if you find anything. :)

---

