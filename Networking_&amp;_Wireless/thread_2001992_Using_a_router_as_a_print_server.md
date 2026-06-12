---
title: "Using a router as a print server?"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by anewguy on 2012-06-11
We now have comcast broadband with their integrated cable modem/phone hookups/wireless router.  We used to use DSL and a NetGear WGR614v9 router.  We had a Dell 1600n printer connected via an ethernet cable to the WGR614v9 router so we could access it from all the computers in the house, and it was working fine.  The phone line, router and printer are in a room of the house with no cable for the cable TV, so the combination access point from comcast was installed by the main TV, and it works fine.  However, now we obviously have no wireless access to the printer the other room.  Any other rooms with cable tv outlets are not appropriate for the printer to be in.  So...... and I know nothing about what I'm trying to ask ...... is there someway to set up the old NetGear router to be wireless to the main router and act as a print server, or at least an access point?


main router -->> wireless -->> netgear router -->> ethernet cable to printer

I don't know if I'm supposed to say access point, print server or what, but just so the printer connects by ethernet cable to the netgear router, the netgear router connects wirelessly to the main router.

I don't even know if this is possible.  I have seen wireless print servers but was wondering if there is a way to accomplish the same thing using the old router since I already paid for it several years ago.

Don't mean to sound stupid - but I have no clue about any of this!

Thanks in advance!

Dave ;)were

---

### Post by anewguy on 2012-06-13
Not that I actually understand it much, but repeated reading online has led me to believe that this can be done if the 2nd router is used as a repeater.  However, it appears that my 2nd router will only run in extemely low or no security to do so, and that is unacceptable to me (it's just the router).

On a side note, I picked up a Dell 3300 print server off Ebay real cheap, but alas I can't get it to work with our network either.  To top it off, it's old enough that it only wants to work with WEP encryption, which again is unacceptable to me.  I'm the device is fine, as well as any newer devices like it - I just happened to pick one too old for my application of it.

So, I'll mark the thread as solved for now.  However - don't be afraid to post here if you can be of help!!  ;)

Thanks!
Dave ;)

---

### Post by dniMretsaM on 2012-06-13
DD-WRT can be used as a print server. [http://www.dd-wrt.com/wiki/index.php/Printer_Sharing](http://www.dd-wrt.com/wiki/index.php/Printer_Sharing). You could install that on your second router (if it's supported) and use that.

You could also hook it up to a computer and just use that to share the printer (over your secured network), but I don't know if that's doable in your setup (if you have a desktop, that would work fine as they would always be connected to the printer).

---

### Post by anewguy on 2012-06-13
I'll have to check that link, then see if the 2nd router can do it.  Currently everyone here has moved to laptops, and all our desktops are gone.  Everyone uses them everywhere except the office, and guess what's in the office? Yep, the printer!  ;)  One of the people said they would just carry their laptop in there when they needed to print, but then wanted to know how to wirelessly scan from the printer - obviously they didn't quite understand the problem ;)

Thanks for the info - I'm going to check that out tonight!

Dave ;)

---

### Post by anewguy on 2012-06-14
Unfortunately my 2nd router isn't supported by DD-WRT, but thank you very much for the information and the reply!

Dave ;)

---

### Post by fyfe54 on 2012-06-14
I extended my network from the front of the house ( basement) to an upstairs rear bedroom using something like this:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6147989&Sku=T156-2570](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6147989&Sku=T156-2570)
Then connected a wireless router/repeater in the bedroom.  Now we can hard wire blueray player and stream Netflix and get strong and fast wireless internet up there.  Maybe you don't even need the wireless router if all you need is an ethernet connection for the printer.

Look into it, it might work for you.

---

### Post by anewguy on 2012-06-14
> **fyfe54 said:**
> I extended my network from the front of the house ( basement) to an upstairs rear bedroom using something like this:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6147989&Sku=T156-2570](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6147989&Sku=T156-2570)
Then connected a wireless router/repeater in the bedroom.  Now we can hard wire blueray player and stream Netflix and get strong and fast wireless internet up there.  Maybe you don't even need the wireless router if all you need is an ethernet connection for the printer.

Look into it, it might work for you.

That's an interesting idea.  When these things first came out I thought they'd be subject to all kinds of electrical noise.  Do they work good for you?  If so, I'm going to give that a try.

Thanks!
Dave ;)

---

### Post by anewguy on 2012-06-24
fyfe54:

Thanks so much!  I bought a couple of used 9650's and it works great!

---

