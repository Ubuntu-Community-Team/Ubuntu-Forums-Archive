---
title: "Two firewire inputs; one source; recording fails"
date: 2008-07-14
forum: Mythbuntu
---

### Post by notadog on 2008-07-14
I have mythbuntu running with video input via a Comcast STB and firewire.  By itself, this configuration works fine with a data source provided by ScheduleDirect (actually a few schedule problems that I'll ignore here).  Now I'm trying to add a pcHDTV card so that I can record multiple shows at the same time on the one myth backend.

In this setup, both inputs are based on Comcast's Palo Alto feed: 
a) firewire out of a STB, and 
b) a pcHDTV card attached to the raw cable feed via a splitter upstream of the STB that I want to use only for unencrypted channels.

From some Myth documentation that I can't now find, I believe I need one source (schedule) for each video input (card).  Furthermore, Mythfilldatabase warns that it is not a good idea to use one source for two inputs. i.e.

2008-07-13 02:12:40.661 SourceUtil::IsProperlyConnected(): Source ID 1 appears to be connected
to 1 scanable input, and 1 non-scanable input. This may be a problem.
2008-07-13 02:12:40.662 SourceUtil::IsProperlyConnected(): Source ID 1 appears to be connected
to both firewire and non-firewire inputs. This is probably a bad idea.

The obvious solution would seem to be to set up a second schedule in Schedule Direct, but their web site won't let me set up two separate source listings based on the one "Comcast Palo Alto" schedule!  When I try to create a second schedule, the "Comcast Palo Alto" source is grayed out (apparently since I've defined one schedule based on it).

When I try using the same schedule for both inputs and record from both at the same time, the FW via the STB works, but the firewire to pcHDTV fails.  In a previous iteration, I've had the pcHDTV working so I'm sure the hardware is ok.

I'd appreciate any suggestion on how to get inputs recording.

Thanks.

---

