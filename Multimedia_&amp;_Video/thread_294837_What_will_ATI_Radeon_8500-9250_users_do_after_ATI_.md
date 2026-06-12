---
title: "What will ATI Radeon 8500-9250 users do after ATI drop the support in fglrx?"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by Turin Turambar on 2006-11-07
Seriously, I didn't plan to upgrade my Radeon 9000pro. It works perfectly and is ok for my needs.

However, ATI announced that they will drop the support in the next fglrx release for cards with R2xx chips.

Did ubuntu hardware team plan anything for those users? I know there'll always be "ati" or "radeon" driver, but that's not a solution if you want good 3D support.

Will it be possible to have two fglrx drivers? One for R2xx (considered older) and one for modern ATI cards (which, of course, would be constantly updated by ATI). That way no one would suffer.

---

### Post by pay on 2006-11-07
You will still be able to use the older fglrx driver for cards that don't support the new driver.

---

### Post by Turin Turambar on 2006-11-07
> **pay said:**
> You will still be able to use the older fglrx driver for cards that don't support the new driver.

That's exactly what I asked - great if it's true! :)
But still doubt this whole thing with old drivers will be useful though - Xorg is developing pretty fast... soon we'll have version 7.2, 7.3... and old fglrx for R2xx won't run there. :(

---

### Post by olley on 2006-11-07
I have got a 9000pro which worked fine in Dapper but not in edgy can only get it to work with the "vesa" drivers

---

### Post by Turin Turambar on 2006-11-07
> **olley said:**
> I have got a 9000pro which worked fine in Dapper but not in edgy can only get it to work with the "vesa" drivers

Did you install restricted package, together with fglrx driver? And did you disable composite in xorg.conf?

Works just flawlessly here...

---

### Post by crashby on 2006-11-07
> **Turin Turambar said:**
> Seriously, I didn't plan to upgrade my Radeon 9000pro. It works perfectly and is ok for my needs.

However, ATI announced that they will drop the support in the next fglrx release for cards with R2xx chips.

Did ubuntu hardware team plan anything for those users? I know there'll always be "ati" or "radeon" driver, but that's not a solution if you want good 3D support.

Will it be possible to have two fglrx drivers? One for R2xx (considered older) and one for modern ATI cards (which, of course, would be constantly updated by ATI). That way no one would suffer.

<script type="text/javascript"><!--
google_ad_client = "pub-9880505107645345";
google_ad_output = "textlink";
google_ad_format = "ref_text";
google_cpa_choice = "CAAQ5KaL_QEaCLVkdeHB3GrAKOzYtIQB";
google_ad_channel = "";
//--></script>
<script type="text/javascript" src="http://pagead2.googlesyndication.com/pagead/show_ads.js">
</script>

---

### Post by crashby on 2006-11-07
<script type="text/javascript"><!--
google_ad_client = "pub-9880505107645345";
google_ad_output = "textlink";
google_ad_format = "ref_text";
google_cpa_choice = "CAAQ5KaL_QEaCLVkdeHB3GrAKOzYtIQB";
google_ad_channel = "";
//--></script>
<script type="text/javascript" src="http://pagead2.googlesyndication.com/pagead/show_ads.js">
</script>

---

### Post by igknighted on 2006-11-07
Supposedly these cards are fully supported by the open source 'radeon' driver included in Xorg... I have a much newer card and use the radeon driver rather than the fglrx driver, mainly on principle, but I find that aiglx support is worth more than any minute speed gains I might get.

---

### Post by Turin Turambar on 2006-11-08
> **igknighted said:**
> Supposedly these cards are fully supported by the open source 'radeon' driver included in Xorg... I have a much newer card and use the radeon driver rather than the fglrx driver, mainly on principle, but I find that aiglx support is worth more than any minute speed gains I might get.

I get much better 3D support with fglrx, than with radeon driver.
As a matter of fact, I didn't even have a 3D support with radeon driver 'till Edgy! But still, fglrx puts nicer and fatter textures.

---

