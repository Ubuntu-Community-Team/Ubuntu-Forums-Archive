---
title: "Remote frontend can't access backend - 'network protocol'??"
date: 2010-08-18
forum: Mythbuntu
---

### Post by zzztownsend on 2010-08-18
OK chaps can you help here, please...?

My remote frontend can't access the the server backend, giving me an error message along the lines of 'network protocol 23056'
My server backend/frontend is still working fine. 

Both machines are 10.04, fully updated, with mythbuntu-repos installed
The only difference is that the server is 32-bit and the remote pc is 64-bit.

The clue I have is that:

on server and remote pc,
mythbuntu-repos is at 8.2-0ubuntu0+mythbuntu~auto20100818002546

but on server (mythbuntu)
mythtv-common is at 0.23.0+fixes25423-0ubuntu0+mythbuntu2

while on remote pc (ubuntu not mythbuntu)
mythtv-common is at 0.23.0+fixes24158-0ubuntu2

So I guess the question is 'how do I align the two?' or 'is fixes25423 going to be released in 64-bit?'

Any help appreciated

Thanks
Matt

---

### Post by zzztownsend on 2010-08-19
OK so partially solved now, by browsing the mythbuntu repositories manually, then manually downloading and installing the *.deb files.

But does anyone know why this would not be working automatically with apt-get update (other updates seem to be OK)

Cheers

matt

---

### Post by ian dobson on 2010-08-19
Hi,

fixes is in both 32 and 64bit. I'm running 64bit on my backend and frontend. My frontend is Mythbuntu and the backend is ubuntu with the mythtv-repos added.

Which mirror are you using? I'm using the DE (Germany/Switzerland) mirror and am at " branches/release-0-23-fixes [25609]" on the backend and "mythfrontend version: branches/release-0-23-fixes [25609]" on the frontend.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-08-19
My guess is that you didn't have autobuilds enabled on your remote frontend. You might think you did, but did not.

---

### Post by zzztownsend on 2010-08-19
Hi thanks for the reply Ian

The output of apt-get update shows
uk.autobuilds.mythbuntu.org

When I go there with a browser, I can find the later version -fixes25423 in both 32 and 64 bit, but even though I've got mythbunt-repos installed, apt is not pulling in the these debs

Cheers
Matt

---

### Post by zzztownsend on 2010-08-19
thanks  tgm4883 it does look like a combinaton of factors
I did a dpkg -i mythbuntu-repos, and now the updates are working, but remote & server still not talking.

an update/upgrade on the server (FROM -fixes25423 TO -fixes25362 (!!!)) has now brought both into line.

Looks like a wobble in the releases, plus my remote mythbuntu-repos turned off were the problems. All sorted now.

Cheers

Matt

---

### Post by tgm4883 on 2010-08-19
> **zzztownsend said:**
> thanks  tgm4883 it does look like a combinaton of factors
I did a dpkg -i mythbuntu-repos, and now the updates are working, but remote & server still not talking.

an update/upgrade on the server (FROM -fixes25423 TO -fixes25362 (!!!)) has now brought both into line.

Looks like a wobble in the releases, plus my remote mythbuntu-repos turned off were the problems. All sorted now.

Cheers

Matt

Yep. Glad it's fixed now. Note that the 0.23.0 ppa isn't getting any more updates. You would have to move to the 0.23.1 PPA. Also note that 0.23.1 isn't compatible with 0.23.0

---

### Post by twin--turbo on 2010-08-22
Mine screwed up a few weeks back, the frontend was having trouble with the repo. I swapped to another and it updated. turned off autobuilds to keep the FE and BE working..

TT

---

### Post by tgm4883 on 2010-08-22
> **twin--turbo said:**
> Mine screwed up a few weeks back, the frontend was having trouble with the repo. I swapped to another and it updated. turned off autobuilds to keep the FE and BE working..

TT

What kind of trouble? All issues with the repo and protocol issues were corrected.

---

