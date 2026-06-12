---
title: "MythWeb TV Listings - NODATA"
date: 2011-11-11
forum: Mythbuntu
---

### Post by nhtrader on 2011-11-11
I'm been using Mythbuntu for a while and recently this problem has surfaced. This is what happens when I try to access my MythBox via Mythweb. I should also add that I use the option that utilizes the channel listing from the TV channel stream. I do not subscribe to any TV schedule service.


1. on remote PC I use the web browser to access my MythBox's MythWeb. Successfull login.
2. Select TV
3. select Program Listing ( or use top menu item Listings)
4. Now all of my channels appear, but every channel contains NODATA. No TV listings appear.

As a possible work around, I tried to access the MythBox via ssh and execute the following command:

mythfilldatabase --refresh-today <E>

Then I refreshed my web browser. This didn't fix the problem.


My current solution, is to call home and get someone to access the Mythbox. 
1. They must enter the Frontend and select Watch TV.
2. then the screen shows NODATA just like MythWeb does.
3. then they must manually use the up or down arrow key to scroll through all of the channels. Only after the cursor highlights the channel will the listings appear and then after a browser refresh the listings appear via MythWeb.

Questions:
1. why does this happen?
2. Is there a way for MythWeb to refresh itself?

---

