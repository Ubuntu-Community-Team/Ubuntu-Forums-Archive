---
title: "2 Extra Encoders Added to DB - HDHOMERUN - 14.04 BUG?"
date: 2015-01-29
forum: Mythbuntu
---

### Post by Kerby_Armand on 2015-01-29
I see 4 encoders in mythweb and in the DB after installing Mythbuntu 14.04.
I've tried this on a few installs, in several different ways.

I use HDHomeRun - I have two different turners and the result using either one is the same.
There are two tuners in the HDHomeRun - so it should only show two encoders.

They are listed in a peculiar way 1 & 3 are really encoder 'a' and 2 & 4 are encoder 'b'.

I have experience with a previous MythTV install with Fedora and the encoders always came in as 1 & 2 and there were only two in the DB as well.

Anyone experience this?
Any Advice?
Is this a bug?

Karmand

EDIT: Found answer today. Multiplexing feature was set incorrectly for HDHomeRun in MythBackEnd Setup - Each tuner for my versions of HDHomeRun should be set to '1' as the number of recordings at a time. Not all HDHomeRuns can multiplex.
NOTE: the default used to be '1' - but after installing and watching the setting the default was set at '2'.

---

