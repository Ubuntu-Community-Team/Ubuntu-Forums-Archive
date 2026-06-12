---
title: "Error: MythTV database has a newer TV schema (1330) than expected (1317)"
date: 2016-08-26
forum: Mythbuntu
---

### Post by alan44 on 2016-08-26
I had Mythbuntu 14.04 running on this machine, but it was getting flaky: some recordings OK, some zero-length, some excessively large and presumably corrupt that would crash the frontend when I tried to play them. I'd applied the various updates that were offered, but they did not cure the problem. Then a day or two ago I was offered the update to 16.04, but that was a disaster, so I saved my recordings to an external drive and ran mythconverg_backup.pl and copied the resulting files to the external drive as well. Then I tried installing 14.04.5 from scratch but the installation failed -- something involving xfsettingsd -- so I installed 14.04.2.  Then I copied over the saved recording files and reinstalled the database. Now I get the error message:Error: MythTV database has a newer TV schema (1330) than expected (1317)and there seems to be no way to prevent the frontend from trying to load and failing and trying to load and failing and... How do i solve this problem? (a) to prevent the frontend from trying to load? (b) get the two schemas in sync?

---

