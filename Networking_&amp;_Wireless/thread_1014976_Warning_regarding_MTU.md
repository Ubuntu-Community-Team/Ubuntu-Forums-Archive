---
title: "Warning regarding MTU"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by chudak on 2008-12-18
I was recently having a problem with my Lenovo T400 on our company vpn. I could connect but was unable to access many of the company intranet applications including exchange webmail and the company intranet (which I surmise was also using active directory for authentication). Curiously I could still SSH to most of the linux servers on our network without issue.

I'm using the vpnc client to connect to a cisco vpn concentrator.

I thought maybe it was some kind of strange problem with my Intel 5300 wifi card and the vpn tunnel. When I switched to a wired connection the problem went away.

Someone at work suggested that it might be an MTU setting problem and  a light bulb went off. Someone on these forums had been peddling the advice to change your MTU to 1430 to resolve some network speed issues and that is what I had done. 

Changing the MTU value back to the default of 1500 resolved the problem immediately.

HTH someone else out there banging their head on the desk for weeks...

Charles

---

### Post by jonobr on 2008-12-18
An interesting post.

I notice you mention 'peddling' of a recommendation to set the MTU to 1430

That is a very odd recommendation , if you look at standards for MTU
you will see the max tx unit for a given media type doesn't have 1430 as one of them.

There is a table here at the MTU wiki.

[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

I usually make recommendations to change MTU when the MTU size is definitely wrong , that is, when a poster submits Ifconfig showing the MTU is well below the min ( and there is a min - I think its 570 or so for dialup connections) 
and their ifconfig shows an ethernet connection.

Thats undoubtedly wrong.
People reading posts after the fact then assume the larger the packet size the large amount of data transferred, which is obviously wrong.
This will increase fragmentation and have a negative impact on their network.

Anyhow, back to the point, the default for ethernet will usually be 1500.
AFAIK VPNs will have an effect on MTU, and usually working with a savvy IT person will be the best way out of this, Im thinking the 1430 MTU post worked for their own specific implementation, not for yours obviously.
Im wondering what actually happened, was it 1500 and then you had problems and set to 1430 based on that post ?

Im thinking if you changed and it didnt work for you , it would have been best to change it back, most monkeying with these settings is a try and see type thing.

Anyway, Good post.....):P

---

### Post by chudak on 2008-12-18
> **jonobr said:**
> An interesting post.

I notice you mention 'peddling' of a recommendation to set the MTU to 1430

I used that term because I think that the suggestion was made without an understanding of the ramifications of it. A variant of "throw a bunch of sh** at the wall and see if something sticks".

> **jonobr said:**
> Anyhow, back to the point, the default for ethernet will usually be 1500. AFAIK VPNs will have an effect on MTU, and usually working with a savvy IT person will be the best way out of this

Ya, but apparently not MY IT person because after two weeks they basically said "we don't know linux so we can't offer you any suggestions as to what is causing the problem and what the solution could be".

> **jonobr said:**
> Im wondering what actually happened, was it 1500 and then you had problems and set to 1430 based on that post ?

Im thinking if you changed and it didnt work for you , it would have been best to change it back, most monkeying with these settings is a try and see type thing.

Yeah, that's what I did and in hindsight, you are right, I should have changed it back, especially after I found the real cause and posted back to the forum... :D

Live and learn....;)

---

### Post by jonobr on 2008-12-22
> Ya, but apparently not MY IT person because after two weeks they basically said "we don't know linux so we can't offer you any suggestions as to what is causing the problem and what the solution could be".

So your typical - I only do this to pay the rent- IT person? :-)

---

### Post by Insane_Homer on 2008-12-22
> **jonobr said:**
> So your typical - I only do this to pay the rent- IT person? :-)

******** and sorry for taking this off topic, but I use Ubuntu in my personal environment but from the business perspective I'm a MS support person. We are an MS house (not my choice). It's not possible to support users outside of the scope of the business. We only support XP as a desktop platform for a very good reason.

I'd like to see try and support 500+ people and let them run any flavour of MS, Linux and Mac and see how you do as a 'pay the rent IT person'.

Half of them have trouble remember their passwords and don't understand the difference between a right click and left click. So have a uniform (and locked down) support environment is very important. having users trolling the internet for solutions and then changing MTU settings on the fly without good reason creates problems that are damned near impossible especially when the reply to simple questions like 'what did change?' are 'nothing, I just...' 

IT is my job and my hobby, but our friend here would have gotten the same response from me and I don't just do it to pay the rent.

---

### Post by jonobr on 2008-12-22
Dont I look like the XXXing idiot:-)

If you do it for fun and its your hobby and job , then your outside the box and a break from the norm ................major kudos.  :guitar:

---

