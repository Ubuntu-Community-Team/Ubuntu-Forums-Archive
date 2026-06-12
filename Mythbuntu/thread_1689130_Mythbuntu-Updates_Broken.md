---
title: "Mythbuntu-Updates Broken?"
date: 2011-02-16
forum: Mythbuntu
---

### Post by melevittfl on 2011-02-16
Is there a problem with the mythbuntu auto builds?

When I do "sudo apt-get update && sudo apt-get upgrade" 

I get many lines like:

Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/0.24/ubuntu/pool/main/m/mythtv/mythtv-theme-arclight_0.24.0+fixes.20110216.316718a-0ubuntu0mythbuntu1_all.deb](http://weeklybuilds.mythbuntu.org/mythbuntu/0.24/ubuntu/pool/main/m/mythtv/mythtv-theme-arclight_0.24.0+fixes.20110216.316718a-0ubuntu0mythbuntu1_all.deb)  Size mismatch
Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/0.24/ubuntu/pool/main/m/mythtv/mythtv-theme-childish_0.24.0+fixes.20110216.316718a-0ubuntu0mythbuntu1_all.deb](http://weeklybuilds.mythbuntu.org/mythbuntu/0.24/ubuntu/pool/main/m/mythtv/mythtv-theme-childish_0.24.0+fixes.20110216.316718a-0ubuntu0mythbuntu1_all.deb)  Size mismatch
Failed to fetch [http://weeklybuilds.mythbuntu.org/mythbuntu/0.24/ubuntu/pool/main/m/mythtv/mythtv-theme-graphite_0.24.0+fixes.20110216.316718a-0ubuntu0mythbuntu1_all.deb](http://weeklybuilds.mythbuntu.org/mythbuntu/0.24/ubuntu/pool/main/m/mythtv/mythtv-theme-graphite_0.24.0+fixes.20110216.316718a-0ubuntu0mythbuntu1_all.deb)  Size mismatch
....

---

### Post by melevittfl on 2011-02-16
Fixed it by running 
sudo dpkg-reconfigure mythbuntu-repos

and picking the PPA repository vs. the DE one...

---

