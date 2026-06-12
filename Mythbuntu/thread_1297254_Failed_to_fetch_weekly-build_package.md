---
title: "Failed to fetch weekly-build package"
date: 2009-10-21
forum: Mythbuntu
---

### Post by JerkyChew on 2009-10-21
Just rebooted into a Mythbuntu box I haven't used in a couple weeks and tried to update my system. I'm pulling from the weekly-builds repos. I received the following:

 Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/pool/main/m/mythtv/libmyth-0.22-0_0.22.0~trunk22374-0ubuntu0~mythbuntu1_amd64.deb](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/pool/main/m/mythtv/libmyth-0.22-0_0.22.0~trunk22374-0ubuntu0~mythbuntu1_amd64.deb)
  404 Not Found

Browsing to that URL I do get a 404 not found. Anybody else having issues?

---

### Post by tgm4883 on 2009-10-21
> **JerkyChew said:**
> Just rebooted into a Mythbuntu box I haven't used in a couple weeks and tried to update my system. I'm pulling from the weekly-builds repos. I received the following:

 Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/pool/main/m/mythtv/libmyth-0.22-0_0.22.0~trunk22374-0ubuntu0~mythbuntu1_amd64.deb](http://weeklybuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu/pool/main/m/mythtv/libmyth-0.22-0_0.22.0~trunk22374-0ubuntu0~mythbuntu1_amd64.deb)
  404 Not Found

Browsing to that URL I do get a 404 not found. Anybody else having issues?

Thats a pretty old package, maybe try an apt-get update?

The latest version is 
0.22.0+fixes22547-0ubuntu0+mythbuntu2

---

### Post by JerkyChew on 2009-10-21
Good call - I was using the Synaptic GUI and even though I hit reload prior to updating I guess it didn't pull down the correct updates. I ran apt-get update and apt-get upgrade from the CLI and everything went through. Thanks!

---

