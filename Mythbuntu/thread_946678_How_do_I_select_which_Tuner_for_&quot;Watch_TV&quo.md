---
title: "How do I select which Tuner for &quot;Watch TV&quot;"
date: 2008-10-13
forum: Mythbuntu
---

### Post by Just4Fun20 on 2008-10-13
This is a really dumb question and I can't believe I can't find the answer.  I'm playing with a digital tuner so now have two tuners in my MythBuntu box.  

When I "Watch TV" it seems to default to the "new" digital tuner (which isn't working).  How can I set it to default to the "old" tuner?  For that matter how can I switch from one tuner to the other?  

Where did this information come from?  I didn't see it in any documentation I have (wiki, forums and installation manual) so I assume I'm missing some important documentation.  

Thanks for any help.

---

### Post by newlinux on 2008-10-13
If you have "avoid conflicts with livetv" option set (or something like that ) then by default the tuner selected for liveTV is the tuner with the highest numbered card ID available. If you don't have that option enabled, it will choose the card with the same hostname first, and then it chooses card with the lowest card ID.

You can switch inputs by pressing "m" and bringing up the menu and scrolling to the item that lets you switch inputs. 

Also, by default in .21 the "y" key switches video sources (it used to switch inputs). So if your 2 cards use 2 different sources pressing Y will switch to the other card. You can change the keybinding in mythweb or in mythfrontend (if you install mythcontrols) to have Y or any key switch inputs.

---

