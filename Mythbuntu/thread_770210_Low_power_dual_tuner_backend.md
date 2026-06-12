---
title: "Low power dual tuner backend"
date: 2008-04-27
forum: Mythbuntu
---

### Post by thusgaard on 2008-04-27
Hi 

I'm in the market for a low power backend. My current backend consumes 160W when ideling. I plan to use mythbuntu because of ease of use. 

In a related project I'll be building new frontends, but first I need a new backend.

My requiremenst: 
2 Tuners 
2 Harddisks (SATA)

Power consumption below 100W, when idle.

I need recomendations for:
- Tuners (Analog PAL)
- Motherboard
- Power supply

Kind regards J;-)

---

### Post by squaregoldfish on 2008-04-27
There's a couple of people on the net who are after the same thing. I came across this the other day:

[http://www.codinghorror.com/blog/archives/001107.html]("http://www.codinghorror.com/blog/archives/001107.html")

Hope it gives you some ideas.

Steve.

---

### Post by thusgaard on 2008-04-27
That looks very interesting... Thanks for the link.

---

### Post by GordonEndersby on 2008-04-27
How about:

Solar panel, storage battery's, 12volt power supply(as used in carputers).
Completely of the grid.
Ive seen a lot of interesting work done recently on 12volt pc power supplies.
The prices have come down a lot, you can even get them on ebay
and of course solar panels have come down a lot as well now.

Gordon

---

### Post by thusgaard on 2008-04-27
Hi Gordon. 

The plan is to make the hardware use as little power as possible. Solar panels are not very efficient in Denmark it rains a lot and my mediacenter has to work in the 3 darkest months of the year. I might get a house mounted windmill instead.... But it will be for more than driving a mediacenter.

J;-)

---

### Post by GordonEndersby on 2008-04-27
Its not so different here in the UK.
Im about to buy some solar panels for camping power and was looking at ways I could use them for the rest of the year and thought a solar powered server would be a good use. I was very impressed with the new solar panels that even here in the UK should provide enough power for a single pc.

Gordon

---

### Post by david_f1976 on 2008-04-28
I suggest you have a read around the forums and reviews on www.silentpcreview.com"].

Also, it is hard to give recommendations without knowing what format you want to go for e.g. mini-ITX, micro-ATX or full-size ATX. Generally, you'll gain features, but also power consumption as you move up format size.

For now I can suggest tuner cards. For analogue, most people would be happy with a Hauppauge 500 or 2x Hauppauge 150s. Hope this helps for now.

---

### Post by thusgaard on 2008-04-28
> **david_f1976 said:**
> it is hard to give recommendations without knowing what format you want to go for e.g. mini-ITX, micro-ATX or full-size ATX. 

For my backend Size is not a problem. The frontend is going to be mini-itx

This was added later, because I just thought of it!!

I have never seen any Mini-itx with 2 PCI sockets.

/This was added later, because I just thought of it!!

---

### Post by david_f1976 on 2008-04-29
Correct, they only usually have 1 slot. However with some cases you can get dual risers. Not sure how advisable this is or if there are any potential issues. Maybe somebody else can advise you there.

If you going for a full-size backend, the choice is then yours for tuners. The Hauppauge-500 will save you the hassle of having to split the incoming tv signal, so that would be my preference.

Getting under 100 watts idle shouldn't be a problem as long as your sensible on component choice. I have an old socket A system which uses just under 100 watts at idle. I'm in the process of creating a new backend using a 120 watt pico-itx power supply, a core 2 duo mobile processor and uses 2 x 500 GB Western Digital Green Power hard drives. It should be possible to use this power supply and hard drives with the motherboard (or similar) linked to in squaregoldfish's post, along with a suitable low power AMD dual core processor. This'll be a cheaper option than the Intel route and should be more than powerful enough.

Again, check out the forums on silentpcreview for more recommendations. Post back if you need links to any of the components mentioned.

---

### Post by amphibem on 2008-04-30
As others has suggested there are a variety of options for your system. All I will say is the system in my sig, which has a fairly high-wattage CPU, runs at around 70W and idles at 52W. 

So with any modern gear, expecially if you avoid discrete graphics cards, you should go well under 100W.

---

