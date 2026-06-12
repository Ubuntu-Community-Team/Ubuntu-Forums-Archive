---
title: "Wirelessly Connected Front-End"
date: 2008-08-11
forum: Mythbuntu
---

### Post by jlp_engineer on 2008-08-11
I have a notebook that I have successfully connected to a combination Front-End/Back-End.  However I cannot seem to be able to watch TV, recorded shows, or even any imported DVD movies.  However, when I take this same notebook and connect to the Back-End via Gigabit Ethernet, watching TV and recorded shows now works, but I still cannot watch imported DVD movies.  Watching imported DVD movies only seems to work when using the local Front-End.  

Am I looking at a bandwidth issue?  If so, how much bandwidth should be necessary to get a remote front-end completely functional?

TIA for any and all suggestions.

---

### Post by volkswagner on 2008-08-11
please provide details.  What type of recordings, SD/HD?  Post log errors.  What happens when you select a recording/TV?
If it is due to bandwidth, others had luck selecting "always stream from backend" in backend setup.
What is you network structure?

---

### Post by jlp_engineer on 2008-08-11
> **volkswagner said:**
> please provide details.  What type of recordings, SD/HD?  Post log errors.  What happens when you select a recording/TV?
If it is due to bandwidth, others had luck selecting "always stream from backend" in backend setup.
What is you network structure?

Well,

All the recordings are SD.  When I select to view TV or a recording, I just get a blank screen for a few moments, and then back to the screen I just left.  

I will try selecting "Always stream from backend" and see if that helps.  

I have a typical 8 port Gigabit switch connected to a wireless router.  I will attempt to look at the logs if I can find them - front end or back end.

---

### Post by novellahub on 2008-08-12
> **jlp_engineer said:**
> Well,

All the recordings are SD.  When I select to view TV or a recording, I just get a blank screen for a few moments, and then back to the screen I just left.  

I will try selecting "Always stream from backend" and see if that helps.  

I have a typical 8 port Gigabit switch connected to a wireless router.  I will attempt to look at the logs if I can find them - front end or back end.

Try changing the playback profiles to either slim or CPU++.  My brother in law had this issue with his machine until he selected the CPU++ profile.

---

### Post by jlp_engineer on 2008-08-13
> **novellahub said:**
> Try changing the playback profiles to either slim or CPU++.  My brother in law had this issue with his machine until he selected the CPU++ profile.

Thank you - I will look at this option and see if this makes any difference.

---

