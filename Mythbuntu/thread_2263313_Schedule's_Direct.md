---
title: "Schedule's Direct"
date: 2015-01-31
forum: Mythbuntu
---

### Post by deanie44 on 2015-01-31
Hi everyone.  I am having a problem downloading guide listings from schedule's direct.  Here is the outcome of a terminal:
```

2015-01-31 02:55:08.408258 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:08.408262 N  We should keep data around after this one
2015-01-31 02:55:08.409169 I  Retrieving datadirect data.
2015-01-31 02:55:08.409183 I  Grabbing data for Sat Jan 31 2015 offset 9
2015-01-31 02:55:08.409199 I  From 2015-02-09T00:00:00Z to 2015-02-10T00:00:00Z (UTC)
2015-01-31 02:55:08.409207 I  DataDirect: Grabbing listing data
2015-01-31 02:55:08.409290 I  Downloading DataDirect feed
2015-01-31 02:55:08.810110 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:08.810118 E  Encountered error in grabbing data.
2015-01-31 02:55:08.810135 I  
2015-01-31 02:55:08.810139 I  Checking day @ offset 10, date: Tue Feb 10 2015
2015-01-31 02:55:08.814314 I  Data refresh needed because no data exists for day @ offset 10 from 8PM - midnight.
2015-01-31 02:55:08.814322 N  Refreshing data for Tue Feb 10 2015
2015-01-31 02:55:08.814333 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:08.814338 N  We should keep data around after this one
2015-01-31 02:55:08.815360 I  Retrieving datadirect data.
2015-01-31 02:55:08.815372 I  Grabbing data for Sat Jan 31 2015 offset 10
2015-01-31 02:55:08.815385 I  From 2015-02-10T00:00:00Z to 2015-02-11T00:00:00Z (UTC)
2015-01-31 02:55:08.815391 I  DataDirect: Grabbing listing data
2015-01-31 02:55:08.815461 I  Downloading DataDirect feed
2015-01-31 02:55:09.216299 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:09.216311 E  Encountered error in grabbing data.
2015-01-31 02:55:09.216337 I  
2015-01-31 02:55:09.216345 I  Checking day @ offset 11, date: Wed Feb 11 2015
2015-01-31 02:55:09.221800 I  Data refresh needed because no data exists for day @ offset 11 from 8PM - midnight.
2015-01-31 02:55:09.221809 N  Refreshing data for Wed Feb 11 2015
2015-01-31 02:55:09.221821 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:09.221826 N  We should keep data around after this one
2015-01-31 02:55:09.222955 I  Retrieving datadirect data.
2015-01-31 02:55:09.222985 I  Grabbing data for Sat Jan 31 2015 offset 11
2015-01-31 02:55:09.223007 I  From 2015-02-11T00:00:00Z to 2015-02-12T00:00:00Z (UTC)
2015-01-31 02:55:09.223018 I  DataDirect: Grabbing listing data
2015-01-31 02:55:09.223125 I  Downloading DataDirect feed
2015-01-31 02:55:09.623957 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:09.623968 E  Encountered error in grabbing data.
2015-01-31 02:55:09.623993 I  
2015-01-31 02:55:09.624001 I  Checking day @ offset 12, date: Thu Feb 12 2015
2015-01-31 02:55:09.629305 I  Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2015-01-31 02:55:09.629313 N  Refreshing data for Thu Feb 12 2015
2015-01-31 02:55:09.629324 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:09.629329 N  We should keep data around after this one
2015-01-31 02:55:09.630445 I  Retrieving datadirect data.
2015-01-31 02:55:09.630462 I  Grabbing data for Sat Jan 31 2015 offset 12
2015-01-31 02:55:09.630483 I  From 2015-02-12T00:00:00Z to 2015-02-13T00:00:00Z (UTC)
2015-01-31 02:55:09.630494 I  DataDirect: Grabbing listing data
2015-01-31 02:55:09.630601 I  Downloading DataDirect feed
2015-01-31 02:55:10.031565 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:10.031576 E  Encountered error in grabbing data.
2015-01-31 02:55:10.031602 I  
2015-01-31 02:55:10.031609 I  Checking day @ offset 13, date: Fri Feb 13 2015
2015-01-31 02:55:10.037110 I  Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2015-01-31 02:55:10.037118 N  Refreshing data for Fri Feb 13 2015
2015-01-31 02:55:10.037130 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:10.037134 N  We should keep data around after this one
2015-01-31 02:55:10.038436 I  Retrieving datadirect data.
2015-01-31 02:55:10.038453 I  Grabbing data for Sat Jan 31 2015 offset 13
2015-01-31 02:55:10.038475 I  From 2015-02-13T00:00:00Z to 2015-02-14T00:00:00Z (UTC)
2015-01-31 02:55:10.038485 I  DataDirect: Grabbing listing data
2015-01-31 02:55:10.038588 I  Downloading DataDirect feed
2015-01-31 02:55:10.439538 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:10.439550 E  Encountered error in grabbing data.
2015-01-31 02:55:10.515885 I  Updating source #2 (tuner 1) with grabber schedulesdirect1
2015-01-31 02:55:10.516064 I  Found 80 channels for source 2 which use grabber
2015-01-31 02:55:10.516087 I  
2015-01-31 02:55:10.516092 I  Checking day @ offset 0, date: Sat Jan 31 2015
2015-01-31 02:55:10.542164 N  Data is already present for Sat Jan 31 2015, skipping
2015-01-31 02:55:10.542182 I  
2015-01-31 02:55:10.542186 I  Checking day @ offset 1, date: Sun Feb 1 2015
2015-01-31 02:55:10.542188 I  Data Refresh always needed for tomorrow
2015-01-31 02:55:10.542191 N  Refreshing data for Sun Feb 1 2015
2015-01-31 02:55:10.542199 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:10.542201 N  We should use cached data for this one
2015-01-31 02:55:10.542991 I  Retrieving datadirect data.
2015-01-31 02:55:10.543003 I  Grabbing data for Sat Jan 31 2015 offset 1
2015-01-31 02:55:10.543016 I  From 2015-02-01T00:00:00Z to 2015-02-02T00:00:00Z (UTC)
2015-01-31 02:55:10.543023 I  DataDirect: Grabbing listing data
2015-01-31 02:55:10.543088 I  Downloading DataDirect feed
2015-01-31 02:55:10.943942 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:10.943955 E  Encountered error in grabbing data.
2015-01-31 02:55:10.943980 I  
2015-01-31 02:55:10.943988 I  Checking day @ offset 2, date: Mon Feb 2 2015
2015-01-31 02:55:10.973162 N  Data is already present for Mon Feb 2 2015, skipping
2015-01-31 02:55:10.973187 I  
2015-01-31 02:55:10.973192 I  Checking day @ offset 3, date: Tue Feb 3 2015
2015-01-31 02:55:10.987301 I  Data refresh needed because only 0 out of 80 channels have at least one program listed for day @ offset 3 from 8PM - midnight.  Previous day had 80 channels with data in that time period.
2015-01-31 02:55:10.987308 N  Refreshing data for Tue Feb 3 2015
2015-01-31 02:55:10.987317 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:10.987319 N  We should use cached data for this one
2015-01-31 02:55:10.987995 I  Retrieving datadirect data.
2015-01-31 02:55:10.988006 I  Grabbing data for Sat Jan 31 2015 offset 3
2015-01-31 02:55:10.988018 I  From 2015-02-03T00:00:00Z to 2015-02-04T00:00:00Z (UTC)
2015-01-31 02:55:10.988026 I  DataDirect: Grabbing listing data
2015-01-31 02:55:10.988091 I  Downloading DataDirect feed
2015-01-31 02:55:11.388869 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:11.388878 E  Encountered error in grabbing data.
2015-01-31 02:55:11.388895 I  
2015-01-31 02:55:11.388899 I  Checking day @ offset 4, date: Wed Feb 4 2015
2015-01-31 02:55:11.391929 I  Data refresh needed because no data exists for day @ offset 4 from 8PM - midnight.
2015-01-31 02:55:11.391934 N  Refreshing data for Wed Feb 4 2015
2015-01-31 02:55:11.391942 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:11.391945 N  We should use cached data for this one
2015-01-31 02:55:11.392634 I  Retrieving datadirect data.
2015-01-31 02:55:11.392644 I  Grabbing data for Sat Jan 31 2015 offset 4
2015-01-31 02:55:11.392655 I  From 2015-02-04T00:00:00Z to 2015-02-05T00:00:00Z (UTC)
2015-01-31 02:55:11.392662 I  DataDirect: Grabbing listing data
2015-01-31 02:55:11.392719 I  Downloading DataDirect feed
2015-01-31 02:55:11.793494 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:11.793502 E  Encountered error in grabbing data.
2015-01-31 02:55:11.793518 I  
2015-01-31 02:55:11.793522 I  Checking day @ offset 5, date: Thu Feb 5 2015
2015-01-31 02:55:11.796546 I  Data refresh needed because no data exists for day @ offset 5 from 8PM - midnight.
2015-01-31 02:55:11.796550 N  Refreshing data for Thu Feb 5 2015
2015-01-31 02:55:11.796558 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:11.796561 N  We should use cached data for this one
2015-01-31 02:55:11.797219 I  Retrieving datadirect data.
2015-01-31 02:55:11.797229 I  Grabbing data for Sat Jan 31 2015 offset 5
2015-01-31 02:55:11.797241 I  From 2015-02-05T00:00:00Z to 2015-02-06T00:00:00Z (UTC)
2015-01-31 02:55:11.797247 I  DataDirect: Grabbing listing data
2015-01-31 02:55:11.797302 I  Downloading DataDirect feed
2015-01-31 02:55:12.198051 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:12.198061 E  Encountered error in grabbing data.
2015-01-31 02:55:12.198079 I  
2015-01-31 02:55:12.198084 I  Checking day @ offset 6, date: Fri Feb 6 2015
2015-01-31 02:55:12.201406 I  Data refresh needed because no data exists for day @ offset 6 from 8PM - midnight.
2015-01-31 02:55:12.201411 N  Refreshing data for Fri Feb 6 2015
2015-01-31 02:55:12.201419 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:12.201422 N  We should use cached data for this one
2015-01-31 02:55:12.202144 I  Retrieving datadirect data.
2015-01-31 02:55:12.202155 I  Grabbing data for Sat Jan 31 2015 offset 6
2015-01-31 02:55:12.202168 I  From 2015-02-06T00:00:00Z to 2015-02-07T00:00:00Z (UTC)
2015-01-31 02:55:12.202175 I  DataDirect: Grabbing listing data
2015-01-31 02:55:12.202234 I  Downloading DataDirect feed
2015-01-31 02:55:12.603058 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:12.603069 E  Encountered error in grabbing data.
2015-01-31 02:55:12.603095 I  
2015-01-31 02:55:12.603103 I  Checking day @ offset 7, date: Sat Feb 7 2015
2015-01-31 02:55:12.607879 I  Data refresh needed because no data exists for day @ offset 7 from 8PM - midnight.
2015-01-31 02:55:12.607884 N  Refreshing data for Sat Feb 7 2015
2015-01-31 02:55:12.607891 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:12.607894 N  We should use cached data for this one
2015-01-31 02:55:12.608932 I  Retrieving datadirect data.
2015-01-31 02:55:12.608942 I  Grabbing data for Sat Jan 31 2015 offset 7
2015-01-31 02:55:12.608954 I  From 2015-02-07T00:00:00Z to 2015-02-08T00:00:00Z (UTC)
2015-01-31 02:55:12.608961 I  DataDirect: Grabbing listing data
2015-01-31 02:55:12.609019 I  Downloading DataDirect feed
2015-01-31 02:55:13.009837 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:13.009848 E  Encountered error in grabbing data.
2015-01-31 02:55:13.009873 I  
2015-01-31 02:55:13.009881 I  Checking day @ offset 8, date: Sun Feb 8 2015
2015-01-31 02:55:13.015216 I  Data refresh needed because no data exists for day @ offset 8 from 8PM - midnight.
2015-01-31 02:55:13.015221 N  Refreshing data for Sun Feb 8 2015
2015-01-31 02:55:13.015229 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:13.015231 N  We should use cached data for this one
2015-01-31 02:55:13.015916 I  Retrieving datadirect data.
2015-01-31 02:55:13.015926 I  Grabbing data for Sat Jan 31 2015 offset 8
2015-01-31 02:55:13.015938 I  From 2015-02-08T00:00:00Z to 2015-02-09T00:00:00Z (UTC)
2015-01-31 02:55:13.015944 I  DataDirect: Grabbing listing data
2015-01-31 02:55:13.016002 I  Downloading DataDirect feed
2015-01-31 02:55:13.416815 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:13.416826 E  Encountered error in grabbing data.
2015-01-31 02:55:13.416852 I  
2015-01-31 02:55:13.416859 I  Checking day @ offset 9, date: Mon Feb 9 2015
2015-01-31 02:55:13.422251 I  Data refresh needed because no data exists for day @ offset 9 from 8PM - midnight.
2015-01-31 02:55:13.422259 N  Refreshing data for Mon Feb 9 2015
2015-01-31 02:55:13.422281 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:13.422287 N  We should use cached data for this one
2015-01-31 02:55:13.423336 I  Retrieving datadirect data.
2015-01-31 02:55:13.423348 I  Grabbing data for Sat Jan 31 2015 offset 9
2015-01-31 02:55:13.423361 I  From 2015-02-09T00:00:00Z to 2015-02-10T00:00:00Z (UTC)
2015-01-31 02:55:13.423369 I  DataDirect: Grabbing listing data
2015-01-31 02:55:13.423433 I  Downloading DataDirect feed
2015-01-31 02:55:13.824246 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:13.824257 E  Encountered error in grabbing data.
2015-01-31 02:55:13.824283 I  
2015-01-31 02:55:13.824290 I  Checking day @ offset 10, date: Tue Feb 10 2015
2015-01-31 02:55:13.829634 I  Data refresh needed because no data exists for day @ offset 10 from 8PM - midnight.
2015-01-31 02:55:13.829642 N  Refreshing data for Tue Feb 10 2015
2015-01-31 02:55:13.829654 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:13.829658 N  We should use cached data for this one
2015-01-31 02:55:13.830758 I  Retrieving datadirect data.
2015-01-31 02:55:13.830775 I  Grabbing data for Sat Jan 31 2015 offset 10
2015-01-31 02:55:13.830795 I  From 2015-02-10T00:00:00Z to 2015-02-11T00:00:00Z (UTC)
2015-01-31 02:55:13.830806 I  DataDirect: Grabbing listing data
2015-01-31 02:55:13.830897 I  Downloading DataDirect feed
2015-01-31 02:55:14.231838 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:14.231850 E  Encountered error in grabbing data.
2015-01-31 02:55:14.231876 I  
2015-01-31 02:55:14.231883 I  Checking day @ offset 11, date: Wed Feb 11 2015
2015-01-31 02:55:14.237229 I  Data refresh needed because no data exists for day @ offset 11 from 8PM - midnight.
2015-01-31 02:55:14.237236 N  Refreshing data for Wed Feb 11 2015
2015-01-31 02:55:14.237247 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:14.237252 N  We should use cached data for this one
2015-01-31 02:55:14.238361 I  Retrieving datadirect data.
2015-01-31 02:55:14.238378 I  Grabbing data for Sat Jan 31 2015 offset 11
2015-01-31 02:55:14.238399 I  From 2015-02-11T00:00:00Z to 2015-02-12T00:00:00Z (UTC)
2015-01-31 02:55:14.238409 I  DataDirect: Grabbing listing data
2015-01-31 02:55:14.238499 I  Downloading DataDirect feed
2015-01-31 02:55:14.639458 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:14.639468 E  Encountered error in grabbing data.
2015-01-31 02:55:14.639494 I  
2015-01-31 02:55:14.639502 I  Checking day @ offset 12, date: Thu Feb 12 2015
2015-01-31 02:55:14.645025 I  Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2015-01-31 02:55:14.645036 N  Refreshing data for Thu Feb 12 2015
2015-01-31 02:55:14.645050 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:14.645054 N  We should use cached data for this one
2015-01-31 02:55:14.646416 I  Retrieving datadirect data.
2015-01-31 02:55:14.646436 I  Grabbing data for Sat Jan 31 2015 offset 12
2015-01-31 02:55:14.646457 I  From 2015-02-12T00:00:00Z to 2015-02-13T00:00:00Z (UTC)
2015-01-31 02:55:14.646469 I  DataDirect: Grabbing listing data
2015-01-31 02:55:14.646567 I  Downloading DataDirect feed
2015-01-31 02:55:15.047541 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:15.047550 E  Encountered error in grabbing data.
2015-01-31 02:55:15.047567 I  
2015-01-31 02:55:15.047571 I  Checking day @ offset 13, date: Fri Feb 13 2015
2015-01-31 02:55:15.050580 I  Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2015-01-31 02:55:15.050585 N  Refreshing data for Fri Feb 13 2015
2015-01-31 02:55:15.050592 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:15.050595 N  We should use cached data for this one
2015-01-31 02:55:15.051548 I  Retrieving datadirect data.
2015-01-31 02:55:15.051565 I  Grabbing data for Sat Jan 31 2015 offset 13
2015-01-31 02:55:15.051586 I  From 2015-02-13T00:00:00Z to 2015-02-14T00:00:00Z (UTC)
2015-01-31 02:55:15.051597 I  DataDirect: Grabbing listing data
2015-01-31 02:55:15.051689 I  Downloading DataDirect feed
2015-01-31 02:55:15.452628 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:15.452640 E  Encountered error in grabbing data.
2015-01-31 02:55:15.529686 I  Updating source #3 (tuner 2) with grabber schedulesdirect1
2015-01-31 02:55:15.529878 I  Found 80 channels for source 3 which use grabber
2015-01-31 02:55:15.529902 I  
2015-01-31 02:55:15.529906 I  Checking day @ offset 0, date: Sat Jan 31 2015
2015-01-31 02:55:15.556232 N  Data is already present for Sat Jan 31 2015, skipping
2015-01-31 02:55:15.556255 I  
2015-01-31 02:55:15.556260 I  Checking day @ offset 1, date: Sun Feb 1 2015
2015-01-31 02:55:15.556263 I  Data Refresh always needed for tomorrow
2015-01-31 02:55:15.556265 N  Refreshing data for Sun Feb 1 2015
2015-01-31 02:55:15.556275 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:15.556278 N  We should use cached data for this one
2015-01-31 02:55:15.556975 I  Retrieving datadirect data.
2015-01-31 02:55:15.556984 I  Grabbing data for Sat Jan 31 2015 offset 1
2015-01-31 02:55:15.556996 I  From 2015-02-01T00:00:00Z to 2015-02-02T00:00:00Z (UTC)
2015-01-31 02:55:15.557004 I  DataDirect: Grabbing listing data
2015-01-31 02:55:15.557068 I  Downloading DataDirect feed
2015-01-31 02:55:15.957962 E[B]  [COLOR=#a52a2a]DataDirect: Failed to get data: Download error[/COLOR]
[/B]2015-01-31 02:55:15.957973 E  Encountered error in grabbing data.
2015-01-31 02:55:15.957999 I  
2015-01-31 02:55:15.958006 I  Checking day @ offset 2, date: Mon Feb 2 2015
2015-01-31 02:55:15.987699 N  Data is already present for Mon Feb 2 2015, skipping
2015-01-31 02:55:15.987725 I  
2015-01-31 02:55:15.987730 I  Checking day @ offset 3, date: Tue Feb 3 2015
2015-01-31 02:55:16.002309 I  Data refresh needed because only 0 out of 80 channels have at least one program listed for day @ offset 3 from 8PM - midnight.  Previous day had 80 channels with data in that time period.
2015-01-31 02:55:16.002317 N  Refreshing data for Tue Feb 3 2015
2015-01-31 02:55:16.002327 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:16.002330 N  We should use cached data for this one
2015-01-31 02:55:16.003049 I  Retrieving datadirect data.
2015-01-31 02:55:16.003061 I  Grabbing data for Sat Jan 31 2015 offset 3
2015-01-31 02:55:16.003073 I  From 2015-02-03T00:00:00Z to 2015-02-04T00:00:00Z (UTC)
2015-01-31 02:55:16.003081 I  DataDirect: Grabbing listing data
2015-01-31 02:55:16.003147 I  Downloading DataDirect feed
2015-01-31 02:55:16.403977 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:16.403988 E  Encountered error in grabbing data.
2015-01-31 02:55:16.404014 I  
2015-01-31 02:55:16.404021 I  Checking day @ offset 4, date: Wed Feb 4 2015
2015-01-31 02:55:16.409445 I  Data refresh needed because no data exists for day @ offset 4 from 8PM - midnight.
2015-01-31 02:55:16.409454 N  Refreshing data for Wed Feb 4 2015
2015-01-31 02:55:16.409466 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:16.409470 N  We should use cached data for this one
2015-01-31 02:55:16.410586 I  Retrieving datadirect data.
2015-01-31 02:55:16.410603 I  Grabbing data for Sat Jan 31 2015 offset 4
2015-01-31 02:55:16.410624 I  From 2015-02-04T00:00:00Z to 2015-02-05T00:00:00Z (UTC)
2015-01-31 02:55:16.410634 I  DataDirect: Grabbing listing data
2015-01-31 02:55:16.410726 I  Downloading DataDirect feed
2015-01-31 02:55:16.811690 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:16.811702 E  Encountered error in grabbing data.
2015-01-31 02:55:16.811728 I  
2015-01-31 02:55:16.811735 I  Checking day @ offset 5, date: Thu Feb 5 2015
2015-01-31 02:55:16.817162 I  Data refresh needed because no data exists for day @ offset 5 from 8PM - midnight.
2015-01-31 02:55:16.817170 N  Refreshing data for Thu Feb 5 2015
2015-01-31 02:55:16.817182 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:16.817186 N  We should use cached data for this one
2015-01-31 02:55:16.818290 I  Retrieving datadirect data.
2015-01-31 02:55:16.818307 I  Grabbing data for Sat Jan 31 2015 offset 5
2015-01-31 02:55:16.818328 I  From 2015-02-05T00:00:00Z to 2015-02-06T00:00:00Z (UTC)
2015-01-31 02:55:16.818338 I  DataDirect: Grabbing listing data
2015-01-31 02:55:16.818429 I  Downloading DataDirect feed
2015-01-31 02:55:17.219382 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:17.219393 E  Encountered error in grabbing data.
2015-01-31 02:55:17.219419 I  
2015-01-31 02:55:17.219426 I  Checking day @ offset 6, date: Fri Feb 6 2015
2015-01-31 02:55:17.224836 I  Data refresh needed because no data exists for day @ offset 6 from 8PM - midnight.
2015-01-31 02:55:17.224843 N  Refreshing data for Fri Feb 6 2015
2015-01-31 02:55:17.224855 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:17.224859 N  We should use cached data for this one
2015-01-31 02:55:17.226016 I  Retrieving datadirect data.
2015-01-31 02:55:17.226034 I  Grabbing data for Sat Jan 31 2015 offset 6
2015-01-31 02:55:17.226056 I  From 2015-02-06T00:00:00Z to 2015-02-07T00:00:00Z (UTC)
2015-01-31 02:55:17.226066 I  DataDirect: Grabbing listing data
2015-01-31 02:55:17.226161 I  Downloading DataDirect feed
2015-01-31 02:55:17.627098 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:17.627106 E  Encountered error in grabbing data.
2015-01-31 02:55:17.627126 I  
2015-01-31 02:55:17.627131 I  Checking day @ offset 7, date: Sat Feb 7 2015
2015-01-31 02:55:17.630797 I  Data refresh needed because no data exists for day @ offset 7 from 8PM - midnight.
2015-01-31 02:55:17.630803 N  Refreshing data for Sat Feb 7 2015
2015-01-31 02:55:17.630812 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:17.630815 N  We should use cached data for this one
2015-01-31 02:55:17.631885 I  Retrieving datadirect data.
2015-01-31 02:55:17.631897 I  Grabbing data for Sat Jan 31 2015 offset 7
2015-01-31 02:55:17.631911 I  From 2015-02-07T00:00:00Z to 2015-02-08T00:00:00Z (UTC)
2015-01-31 02:55:17.631919 I  DataDirect: Grabbing listing data
2015-01-31 02:55:17.631987 I  Downloading DataDirect feed
2015-01-31 02:55:18.032818 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:18.032826 E  Encountered error in grabbing data.
2015-01-31 02:55:18.032844 I  
2015-01-31 02:55:18.032848 I  Checking day @ offset 8, date: Sun Feb 8 2015
2015-01-31 02:55:18.035919 I  Data refresh needed because no data exists for day @ offset 8 from 8PM - midnight.
2015-01-31 02:55:18.035923 N  Refreshing data for Sun Feb 8 2015
2015-01-31 02:55:18.035931 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:18.035934 N  We should use cached data for this one
2015-01-31 02:55:18.036599 I  Retrieving datadirect data.
2015-01-31 02:55:18.036609 I  Grabbing data for Sat Jan 31 2015 offset 8
2015-01-31 02:55:18.036621 I  From 2015-02-08T00:00:00Z to 2015-02-09T00:00:00Z (UTC)
2015-01-31 02:55:18.036628 I  DataDirect: Grabbing listing data
2015-01-31 02:55:18.036683 I  Downloading DataDirect feed
2015-01-31 02:55:18.437478 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:18.437490 E  Encountered error in grabbing data.
2015-01-31 02:55:18.437517 I  
2015-01-31 02:55:18.437524 I  Checking day @ offset 9, date: Mon Feb 9 2015
2015-01-31 02:55:18.443003 I  Data refresh needed because no data exists for day @ offset 9 from 8PM - midnight.
2015-01-31 02:55:18.443014 N  Refreshing data for Mon Feb 9 2015
2015-01-31 02:55:18.443027 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:18.443031 N  We should use cached data for this one
2015-01-31 02:55:18.444397 I  Retrieving datadirect data.
2015-01-31 02:55:18.444417 I  Grabbing data for Sat Jan 31 2015 offset 9
2015-01-31 02:55:18.444439 I  From 2015-02-09T00:00:00Z to 2015-02-10T00:00:00Z (UTC)
2015-01-31 02:55:18.444450 I  DataDirect: Grabbing listing data
2015-01-31 02:55:18.444550 I  Downloading DataDirect feed
2015-01-31 02:55:18.845558 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:18.845569 E  Encountered error in grabbing data.
2015-01-31 02:55:18.845597 I  
2015-01-31 02:55:18.845604 I  Checking day @ offset 10, date: Tue Feb 10 2015
2015-01-31 02:55:18.851032 I  Data refresh needed because no data exists for day @ offset 10 from 8PM - midnight.
2015-01-31 02:55:18.851040 N  Refreshing data for Tue Feb 10 2015
2015-01-31 02:55:18.851052 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:18.851056 N  We should use cached data for this one
2015-01-31 02:55:18.852182 I  Retrieving datadirect data.
2015-01-31 02:55:18.852201 I  Grabbing data for Sat Jan 31 2015 offset 10
2015-01-31 02:55:18.852223 I  From 2015-02-10T00:00:00Z to 2015-02-11T00:00:00Z (UTC)
2015-01-31 02:55:18.852233 I  DataDirect: Grabbing listing data
2015-01-31 02:55:18.852324 I  Downloading DataDirect feed
2015-01-31 02:55:19.253295 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:19.253306 E  Encountered error in grabbing data.
2015-01-31 02:55:19.253333 I  
2015-01-31 02:55:19.253340 I  Checking day @ offset 11, date: Wed Feb 11 2015
2015-01-31 02:55:19.258793 I  Data refresh needed because no data exists for day @ offset 11 from 8PM - midnight.
2015-01-31 02:55:19.258800 N  Refreshing data for Wed Feb 11 2015
2015-01-31 02:55:19.258812 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:19.258816 N  We should use cached data for this one
2015-01-31 02:55:19.259980 I  Retrieving datadirect data.
2015-01-31 02:55:19.259997 I  Grabbing data for Sat Jan 31 2015 offset 11
2015-01-31 02:55:19.260019 I  From 2015-02-11T00:00:00Z to 2015-02-12T00:00:00Z (UTC)
2015-01-31 02:55:19.260029 I  DataDirect: Grabbing listing data
2015-01-31 02:55:19.260121 I  Downloading DataDirect feed
2015-01-31 02:55:19.661089 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:19.661100 E  Encountered error in grabbing data.
2015-01-31 02:55:19.661126 I  
2015-01-31 02:55:19.661134 I  Checking day @ offset 12, date: Thu Feb 12 2015
2015-01-31 02:55:19.666566 I  Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2015-01-31 02:55:19.666574 N  Refreshing data for Thu Feb 12 2015
2015-01-31 02:55:19.666585 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:19.666589 N  We should use cached data for this one
2015-01-31 02:55:19.667738 I  Retrieving datadirect data.
2015-01-31 02:55:19.667755 I  Grabbing data for Sat Jan 31 2015 offset 12
2015-01-31 02:55:19.667776 I  From 2015-02-12T00:00:00Z to 2015-02-13T00:00:00Z (UTC)
2015-01-31 02:55:19.667786 I  DataDirect: Grabbing listing data
2015-01-31 02:55:19.667878 I  Downloading DataDirect feed
2015-01-31 02:55:20.068854 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:20.068866 E  Encountered error in grabbing data.
2015-01-31 02:55:20.068892 I  
2015-01-31 02:55:20.068899 I  Checking day @ offset 13, date: Fri Feb 13 2015
2015-01-31 02:55:20.073295 I  Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2015-01-31 02:55:20.073301 N  Refreshing data for Fri Feb 13 2015
2015-01-31 02:55:20.073311 I  This DataDirect listings source is shared by 3 MythTV lineups
2015-01-31 02:55:20.073314 N  We should use cached data for this one
2015-01-31 02:55:20.074089 I  Retrieving datadirect data.
2015-01-31 02:55:20.074101 I  Grabbing data for Sat Jan 31 2015 offset 13
2015-01-31 02:55:20.074116 I  From 2015-02-13T00:00:00Z to 2015-02-14T00:00:00Z (UTC)
2015-01-31 02:55:20.074123 I  DataDirect: Grabbing listing data
2015-01-31 02:55:20.074190 I  Downloading DataDirect feed
2015-01-31 02:55:20.475058 E  DataDirect: Failed to get data: Download error
2015-01-31 02:55:20.475068 E  Encountered error in grabbing data.
2015-01-31 02:55:20.475475 E  Failed to fetch some program info
2015-01-31 02:55:20.475501 I  Adjusting program database end times.
2015-01-31 02:55:20.476515 I      0 replacements made
2015-01-31 02:55:20.476520 I  Marking generic episodes.
2015-01-31 02:55:20.820074 I      Found 0
2015-01-31 02:55:20.820082 I  Extending non-unique programids with multiple parts.
2015-01-31 02:55:20.893538 I      Found 0
2015-01-31 02:55:20.893544 I  Fixing missing original airdates.
2015-01-31 02:55:21.499674 I      Found 0 with programids
2015-01-31 02:55:21.500636 I      Found 0 without programids
2015-01-31 02:55:21.500640 I  Marking repeats.
2015-01-31 02:55:21.671137 I      Found 0
2015-01-31 02:55:21.671145 I  Unmarking new episode rebroadcast repeats.
2015-01-31 02:55:21.847546 I      Found 0
2015-01-31 02:55:22.879857 I  Marking episode first showings.
2015-01-31 02:55:24.109251 I      Found 57840
2015-01-31 02:55:24.109258 I  Marking episode last showings.
2015-01-31 02:55:25.562439 I      Found 57795
2015-01-31 02:55:25.576616 I  DataDirect: Grabbing next suggested grabbing time
2015-01-31 02:55:25.977585 E  DataDirect: GrabNextSuggestedTime: Could not download
2015-01-31 02:55:25.977605 I  
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2015-01-31 02:55:25.978789 N  mythfilldatabase run complete.
2015-01-31 02:55:25.978886 I  Waiting for threads to exit.
deanie56@deanie56-Inspiron-560:~$ 

```
I have tried several times to add channel 1332-Bravo--and cannot add it.  I also changed my password on Schedule's Direct.  Could that be the reason I am not receiving any new data?  Any help will be appreciated.  deanie44

---

### Post by uteck on 2015-01-31
If you did not update the Myth server with the new password, that would stop it from logging in.
Another option might be that the channel is disabled in your settings, either in Myth or Schedule Direct.  I disabled some of the channels in Schedules Direct but as channels were moved around or added, I have to manually select them to be included in my download.

---

### Post by deanie44 on 2015-01-31
uteck. thank you for answering my post.  how do you update the Myth server with your new password?  deanie44

---

### Post by captain_video on 2015-01-31
You need to exit the MythTV Frontend and get to the Video Sources setup in the MythTV Backend.  You enter your Schedules Direct user name and password there so it can log in automatically to retrieve the guide data from your account.

---

