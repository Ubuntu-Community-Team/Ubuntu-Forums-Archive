---
title: "Mythbuntu - Comcast Loudoun Co/Sterling - Digital lineup - problem!"
date: 2008-02-20
forum: Mythbuntu
---

### Post by dimka2000 on 2008-02-20
I got mythbuntu 7.10 with Avermedia A180.
For whatever reason the scan tool from dvb-utils is not picking up anything for me, so I can't try the scan -> channels.conf -> import to MythTV route
MythTV channel scan seems to be working OK.
Problems:
1) the transport list it's relying on doesn't seem to be complete as it misses a number of DT and HD channels (for Comcast here, it's QAM256 High  HRC).
2) the channels it does find have weird channel numbers, not even close to the channel numbers on comcast or schedulesdirect channel lists. So, is that why when I do ''Fetch channels from listings source" after the channels scan - it does not do anything?

below is the channel list that I manually compiled (I did not include music channels and PPV).
Per my first problem above, some channel are found by my TV tuner, but not by the A180 (largest continuous groups missing being MHz 192-197 and HD stuff 232-251).

comcast/SD ch# | chl# as found by A180 & my TV | ch desc | detected by A180
119	75.12			LMN		                yes
123	80.8			Oxygen			yes
138	80.6			AMC			yes
149	119.6			MoviePlex			yes
178	119.2			CNBC World		yes
192	126.2			MHz2 Russian World		no
193	126.3			MHz3 France24		no
194	126.4			MHz4 Nigerian TV Authority	no
195	126.5			MHz5 Russia Today		no
196	126.6			MHz6 NHK World TV	                no
197	126.1			WNVC MHz Worldview	no
198	119.3			WQAW-69 (Azteca America)	no
200	26.2			WETA Create		yes
201	26.3			WETA Family		yes
202	26.4			WETA World		yes
203	?			WUSA 9 Live Radar		yes
204	?			Doug Hill's Weather Now	yes
205	?			WJLA Local Point		no
208	117.7			NBC Weather Plus		yes
210	7.5			WJLA-HD (ABC)		yes
211	4.1			WRC-HD (NBC)		yes
212	9.1			WUSA-HD (CBS)		yes
213	5.2			WTTG-HD (FOX)		yes
214	3.1			WDCW-HD (CW)		no
215	20.2			WDCA-DTHD (My)		yes
220	26.1			WETA-HD (PBS)		yes
223	?			A&E HD			yes
225	?			HD Theater		yes
229	75.1202			HGTV HD			?
231	76.1302			Food Network HD		yes
232	?			TBS HD			?
234	129.4001		                CNN HD 			no
235	132.3901		                USA HD			no
236	132.3902		                Sci-Fi Channel HD		no
237	129.4002		                History HD			no
239	103.4102		                Discovery HD		no
240	130.410			TLC HD			no
241	131.4201		                Animal Planet HD		no
251	121.6			CSNDCHD			no
254	125.5			GolfVS ?			yes	
?	75.12			LMN			no

Would appreciate any help!
If someone out there uses this lineup , could you share the transport information or channels.conf? So I could import or manually add the missing channels?

Thanks!

---

