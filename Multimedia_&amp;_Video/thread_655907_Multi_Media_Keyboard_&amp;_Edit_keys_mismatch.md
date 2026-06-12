---
title: "Multi Media Keyboard &amp; Edit keys mismatch"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by timdf911 on 2008-01-01
SOLVED-

sort of....

By mapping the special function keys to F13 and upwards, Edit keys in Mythbuntu now recognizes them all correctly - still puzzled as to why XF86Launch0 etc were troublesome though.

++++++++++++++++++++++++++++++++++
Original message:

Not sure if this is the right forum - but here goes..

I have a BTC wireless multimedia keyboard I'm using with Mythbuntu.

By tweaking my xorg.conf file plus making my own xmodmap file I've been able to get Ubuntu to correctly recognize all the 'special keys'.

I had to resort to giving them existing XF86 key symbol names, so they are called XF86Launch0 thru to XF86LaunchF.

FYI I did give them more meaningful custom names such as 'PrgGuide' in XkeysymDB - and they were recognized ok in Ubuntu's key short cuts - but not in Mythbuntu.

Now here's the rub - I named them XF86Launch0 thru to XF86LaunchF but Mythbuntu recognizes them in Key edit as XF86Launch(2) thru to XF86Launch(F).

The references are offset by two and Mythbuntu insists in putting () round the numbers.  This means I can't use the last two keys.

I've checked the mapping using XEV and looked for duplicates in xmodmap which might have thrown the mapping off.  All seems ok.

Three questions - 

When I used customed custom keysymbol names, why didn't Mythbuntu  recognize them ? 

Does Mythbuntu cross check with some other files besides XKeysymDB ?

Why does Mythbuntu not use the keysyms as entered, ie XF86Launch0 versus XF86Launch(0) ?

Sure have learnt a lot these past fews days - if I can get these questions answered, it could make for a good how to (or how not to !).

All this is on Gutsy 7.10.


Regards Tim

---

