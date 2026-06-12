---
title: "Secondary Backend populates channels but no tuners"
date: 2011-05-12
forum: Multimedia Software
---

### Post by vidtek on 2011-05-12
I put this up on a previous thread in March, no replies.  Then I was using 23 fixes.

I updated to 24 fixes and still get this problem.

Setup:

64-bit Mythbuntu 24 fixes on old AMD master backend.  

32-bit Ultimate 29 24 fixes with 2.6.35-29-generic-pae kernel on i7 newish box front/backend.

USB Compro U300 and Divico PCI HDTV card on master backend.

Hauppauge HR2200 on frontend/secondary.

Everything works beautifully except the Hauppauge tuner fails to show up in either the backend or frontend boxes using live tv and won't record using it..

When I run mythtv-setup on the secondary, the Hauppauge card finds all the local channels and populates the database, and also comes up in the video sources setup screen on both backends.

The card works perfectly using Kaffiene.

I have removed all cards from the database many times and rescanned channels but no go.

Anyone any ideas?

Tony.

---

### Post by vidtek on 2011-10-20
> **vidtek said:**
> I put this up on a previous thread in March, no replies.  Then I was using 23 fixes.

I updated to 24 fixes and still get this problem.

Setup:

64-bit Mythbuntu 24 fixes on old AMD master backend.  

32-bit Ultimate 29 24 fixes with 2.6.35-29-generic-pae kernel on i7 newish box front/backend.

USB Compro U300 and Divico PCI HDTV card on master backend.

Hauppauge HR2200 on frontend/secondary.

Everything works beautifully except the Hauppauge tuner fails to show up in either the backend or frontend boxes using live tv and won't record using it..



Tony.

20-10-2011
OK marking this as solved.

I read somewhere not to run mythfilldatabase on slave backends.  So I  have been zealous in my efforts not to do this.  All I had to do was run  mythfilldatabase on my secondary backend and it all works beautifully  now all tuners work great.

Tony.

---

