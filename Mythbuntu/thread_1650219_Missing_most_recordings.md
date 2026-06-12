---
title: "Missing most recordings"
date: 2010-12-21
forum: Mythbuntu
---

### Post by tonycollinet on 2010-12-21
Seem to be missing most recordings for the last few days. EG a recording was supposed to start at 14:19 today, but didn't. Backend log for a few minutes either side is shown below - I can't see anything obvious at that time - but I'm getting a lot of get_playback_url errors

Any ideas what to look for ?

Thanks.





> 2010-12-21 14:02:05.267 AutoExpire: CalcParams(): Max required Free Space: 30.0 GB w/freq: 15 min
2010-12-21 14:04:27.768 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-12-21 14:04:27.957 UPnpMedia: BuildMediaMap Done. Found 212 objects
2010-12-21 14:16:08.402 MainServer::ANN Monitor
2010-12-21 14:16:08.442 adding: myth as a client (events: 2)
2010-12-21 14:17:02.127 MainServer::ANN Monitor
2010-12-21 14:17:02.182 adding: myth as a client (events: 0)
2010-12-21 14:17:05.408 AutoExpire: CalcParams(): Max required Free Space: 30.0 GB w/freq: 15 min
2010-12-21 14:32:05.614 AutoExpire: CalcParams(): Max required Free Space: 30.0 GB w/freq: 15 min
2010-12-21 14:33:29.728 MainServer::ANN Monitor
2010-12-21 14:33:29.770 adding: myth as a client (events: 2)
2010-12-21 14:34:03.769 MainServer::ANN Monitor
2010-12-21 14:34:03.808 adding: myth as a client (events: 2)
2010-12-21 14:34:04.789 MainServer::ANN Monitor
2010-12-21 14:34:04.817 adding: myth as a client (events: 2)
2010-12-21 14:34:05.085 ProgramInfo(1001_20101218222700.mpg), Error: GetPlaybackURL: '1001_20101218222700.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.121 ProgramInfo(1019_20101218222601.mpg), Error: GetPlaybackURL: '1019_20101218222601.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.155 ProgramInfo(1019_20101218222600.mpg), Error: GetPlaybackURL: '1019_20101218222600.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.191 ProgramInfo(1019_20101216190200.mpg), Error: GetPlaybackURL: '1019_20101216190200.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.231 ProgramInfo(1019_20101216190100.mpg), Error: GetPlaybackURL: '1019_20101216190100.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.266 ProgramInfo(1028_20101213233201.mpg), Error: GetPlaybackURL: '1028_20101213233201.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.307 ProgramInfo(1029_20101213233201.mpg), Error: GetPlaybackURL: '1029_20101213233201.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.339 ProgramInfo(1028_20101213233200.mpg), Error: GetPlaybackURL: '1028_20101213233200.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.373 ProgramInfo(1028_20101213233102.mpg), Error: GetPlaybackURL: '1028_20101213233102.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.407 ProgramInfo(1028_20101213233101.mpg), Error: GetPlaybackURL: '1028_20101213233101.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.449 ProgramInfo(1029_20101213233101.mpg), Error: GetPlaybackURL: '1029_20101213233101.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.493 ProgramInfo(1019_20101213233100.mpg), Error: GetPlaybackURL: '1019_20101213233100.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.543 ProgramInfo(1019_20101204202201.mpg), Error: GetPlaybackURL: '1019_20101204202201.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.585 ProgramInfo(1001_20101204202101.mpg), Error: GetPlaybackURL: '1001_20101204202101.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.627 ProgramInfo(1028_20101204202101.mpg), Error: GetPlaybackURL: '1028_20101204202101.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.668 ProgramInfo(1019_20101204202100.mpg), Error: GetPlaybackURL: '1019_20101204202100.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.710 ProgramInfo(1003_20101204202100.mpg), Error: GetPlaybackURL: '1003_20101204202100.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.759 ProgramInfo(1019_20101123061702.mpg), Error: GetPlaybackURL: '1019_20101123061702.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.803 ProgramInfo(1019_20101123061701.mpg), Error: GetPlaybackURL: '1019_20101123061701.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.845 ProgramInfo(1019_20101122185902.mpg), Error: GetPlaybackURL: '1019_20101122185902.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.877 ProgramInfo(1028_20101122185902.mpg), Error: GetPlaybackURL: '1028_20101122185902.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.911 ProgramInfo(1019_20101122185901.mpg), Error: GetPlaybackURL: '1019_20101122185901.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.953 ProgramInfo(1028_20101122185901.mpg), Error: GetPlaybackURL: '1028_20101122185901.mpg' should be local, but it can not be found.
2010-12-21 14:34:05.987 ProgramInfo(1019_20101122185900.mpg), Error: GetPlaybackURL: '1019_20101122185900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.020 ProgramInfo(1002_20101122185900.mpg), Error: GetPlaybackURL: '1002_20101122185900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.062 ProgramInfo(1019_20101121123800.mpg), Error: GetPlaybackURL: '1019_20101121123800.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.095 ProgramInfo(1001_20101115091200.mpg), Error: GetPlaybackURL: '1001_20101115091200.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.137 ProgramInfo(1019_20101113161501.mpg), Error: GetPlaybackURL: '1019_20101113161501.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.172 ProgramInfo(1019_20101113161500.mpg), Error: GetPlaybackURL: '1019_20101113161500.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.205 ProgramInfo(1019_20101112045800.mpg), Error: GetPlaybackURL: '1019_20101112045800.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.238 ProgramInfo(1019_20101111213900.mpg), Error: GetPlaybackURL: '1019_20101111213900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.272 ProgramInfo(1019_20101108041202.mpg), Error: GetPlaybackURL: '1019_20101108041202.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.307 ProgramInfo(1001_20101108041200.mpg), Error: GetPlaybackURL: '1001_20101108041200.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.339 ProgramInfo(1019_20101108041200.mpg), Error: GetPlaybackURL: '1019_20101108041200.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.372 ProgramInfo(1007_20101108041200.mpg), Error: GetPlaybackURL: '1007_20101108041200.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.409 ProgramInfo(1003_20101108041100.mpg), Error: GetPlaybackURL: '1003_20101108041100.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.448 ProgramInfo(1001_20101102230901.mpg), Error: GetPlaybackURL: '1001_20101102230901.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.482 ProgramInfo(1019_20101102230900.mpg), Error: GetPlaybackURL: '1019_20101102230900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.517 ProgramInfo(1028_20101102230802.mpg), Error: GetPlaybackURL: '1028_20101102230802.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.557 ProgramInfo(1028_20101102230801.mpg), Error: GetPlaybackURL: '1028_20101102230801.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.599 ProgramInfo(1028_20101101190302.mpg), Error: GetPlaybackURL: '1028_20101101190302.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.641 ProgramInfo(1028_20101101190301.mpg), Error: GetPlaybackURL: '1028_20101101190301.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.683 ProgramInfo(1003_20101020210910.mpg), Error: GetPlaybackURL: '1003_20101020210910.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.726 ProgramInfo(1003_20101020210857.mpg), Error: GetPlaybackURL: '1003_20101020210857.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.766 ProgramInfo(1028_20101020202800.mpg), Error: GetPlaybackURL: '1028_20101020202800.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.808 ProgramInfo(1028_20101020201300.mpg), Error: GetPlaybackURL: '1028_20101020201300.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.863 ProgramInfo(1019_20100723005900.mpg), Error: GetPlaybackURL: '1019_20100723005900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.904 ProgramInfo(1019_20100723001900.mpg), Error: GetPlaybackURL: '1019_20100723001900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.936 ProgramInfo(1019_20100722233900.mpg), Error: GetPlaybackURL: '1019_20100722233900.mpg' should be local, but it can not be found.
2010-12-21 14:34:06.970 ProgramInfo(1007_20100722232400.mpg), Error: GetPlaybackURL: '1007_20100722232400.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.004 ProgramInfo(1019_20100722225900.mpg), Error: GetPlaybackURL: '1019_20100722225900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.037 ProgramInfo(1007_20100722225800.mpg), Error: GetPlaybackURL: '1007_20100722225800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.079 ProgramInfo(1019_20100722221900.mpg), Error: GetPlaybackURL: '1019_20100722221900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.113 ProgramInfo(1019_20100722214400.mpg), Error: GetPlaybackURL: '1019_20100722214400.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.146 ProgramInfo(1019_20100722213900.mpg), Error: GetPlaybackURL: '1019_20100722213900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.179 ProgramInfo(1019_20100722205800.mpg), Error: GetPlaybackURL: '1019_20100722205800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.214 ProgramInfo(1003_20100722122900.mpg), Error: GetPlaybackURL: '1003_20100722122900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.247 ProgramInfo(1003_20100722112900.mpg), Error: GetPlaybackURL: '1003_20100722112900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.280 ProgramInfo(1003_20100722102800.mpg), Error: GetPlaybackURL: '1003_20100722102800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.314 ProgramInfo(1028_20100722072800.mpg), Error: GetPlaybackURL: '1028_20100722072800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.348 ProgramInfo(1019_20100722001800.mpg), Error: GetPlaybackURL: '1019_20100722001800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.381 ProgramInfo(1007_20100721231900.mpg), Error: GetPlaybackURL: '1007_20100721231900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.414 ProgramInfo(1007_20100721225800.mpg), Error: GetPlaybackURL: '1007_20100721225800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.448 ProgramInfo(1019_20100721213900.mpg), Error: GetPlaybackURL: '1019_20100721213900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.483 ProgramInfo(1019_20100721205800.mpg), Error: GetPlaybackURL: '1019_20100721205800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.525 ProgramInfo(1003_20100721122900.mpg), Error: GetPlaybackURL: '1003_20100721122900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.566 ProgramInfo(1003_20100721112900.mpg), Error: GetPlaybackURL: '1003_20100721112900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.608 ProgramInfo(1003_20100721102800.mpg), Error: GetPlaybackURL: '1003_20100721102800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.649 ProgramInfo(1028_20100721072800.mpg), Error: GetPlaybackURL: '1028_20100721072800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.691 ProgramInfo(1007_20100720234900.mpg), Error: GetPlaybackURL: '1007_20100720234900.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.733 ProgramInfo(1007_20100720232800.mpg), Error: GetPlaybackURL: '1007_20100720232800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.775 ProgramInfo(1019_20100720205800.mpg), Error: GetPlaybackURL: '1019_20100720205800.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.817 ProgramInfo(1019_20100720042108.mpg), Error: GetPlaybackURL: '1019_20100720042108.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.858 ProgramInfo(1019_20100720042106.mpg), Error: GetPlaybackURL: '1019_20100720042106.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.902 ProgramInfo(1019_20100720042105.mpg), Error: GetPlaybackURL: '1019_20100720042105.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.942 ProgramInfo(1019_20100720042104.mpg), Error: GetPlaybackURL: '1019_20100720042104.mpg' should be local, but it can not be found.
2010-12-21 14:34:07.984 ProgramInfo(1019_20100720042103.mpg), Error: GetPlaybackURL: '1019_20100720042103.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.026 ProgramInfo(1019_20100720042102.mpg), Error: GetPlaybackURL: '1019_20100720042102.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.061 ProgramInfo(1019_20100720042101.mpg), Error: GetPlaybackURL: '1019_20100720042101.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.101 ProgramInfo(1024_20100621172800.mpg), Error: GetPlaybackURL: '1024_20100621172800.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.143 ProgramInfo(1003_20100610112900.mpg), Error: GetPlaybackURL: '1003_20100610112900.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.185 ProgramInfo(1004_20100610112900.mpg), Error: GetPlaybackURL: '1004_20100610112900.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.227 ProgramInfo(1004_20100610105900.mpg), Error: GetPlaybackURL: '1004_20100610105900.mpg' should be local, but it can not be found.
2010-12-21 14:34:08.266 ProgramInfo(1028_20100610072800.mpg), Error: GetPlaybackURL: '1028_20100610072800.mpg' should be local, but it can not be found.
2010-12-21 14:34:10.597 MainServer::ANN Monitor
2010-12-21 14:34:10.626 adding: myth as a client (events: 2)
2010-12-21 14:34:16.118 ProgramInfo(): Updated pathname '':'' -> '1019_20101219193800.mpg'
2010-12-21 14:34:16.231 ProgramInfo(): Updated pathname '':'' -> '1001_20101221093400.mpg'
2010-12-21 14:34:16.350 ProgramInfo(): Updated pathname '':'' -> '1007_20101221032300.mpg'
2010-12-21 14:34:16.369 ProgramInfo(): Updated pathname '':'' -> '1019_20101220141900.mpg'
2010-12-21 14:34:16.484 ProgramInfo(): Updated pathname '':'' -> '1019_20101220133800.mpg'
2010-12-21 14:34:16.870 ProgramInfo(): Updated pathname '':'' -> '1007_20101219030900.mpg'
2010-12-21 14:34:16.938 ProgramInfo(): Updated pathname '':'' -> '1007_20101219024300.mpg'
2010-12-21 14:34:17.163 ProgramInfo(): Updated pathname '':'' -> '1007_20101219020300.mpg'
2010-12-21 14:34:17.222 ProgramInfo(): Updated pathname '':'' -> '1019_20101219012300.mpg'
2010-12-21 14:34:17.580 ProgramInfo(): Updated pathname '':'' -> '1001_20101218222700.mpg'
2010-12-21 14:34:17.618 ProgramInfo(1001_20101218222700.mpg), Error: GetPlaybackURL: '1001_20101218222700.mpg' should be local, but it can not be found.
2010-12-21 14:34:17.784 ProgramInfo(): Updated pathname '':'' -> '1019_20101218222601.mpg'
2010-12-21 14:34:17.817 ProgramInfo(1019_20101218222601.mpg), Error: GetPlaybackURL: '1019_20101218222601.mpg' should be local, but it can not be found.
2010-12-21 14:34:17.822 ProgramInfo(): Updated pathname '':'' -> '1019_20101218222600.mpg'
2010-12-21 14:34:17.885 ProgramInfo(1019_20101218222600.mpg), Error: GetPlaybackURL: '1019_20101218222600.mpg' should be local, but it can not be found.
2010-12-21 14:34:18.000 ProgramInfo(): Updated pathname '':'' -> '1003_20101218092800.mpg'
2010-12-21 14:34:18.044 ProgramInfo(): Updated pathname '':'' -> '1007_20101217235400.mpg'
2010-12-21 14:34:18.371 ProgramInfo(): Updated pathname '':'' -> '1019_20101217233800.mpg'
2010-12-21 14:34:18.578 ProgramInfo(): Updated pathname '':'' -> '1007_20101217232800.mpg'
2010-12-21 14:34:18.665 ProgramInfo(): Updated pathname '':'' -> '1019_20101217221800.mpg'
2010-12-21 14:34:18.818 ProgramInfo(): Updated pathname '':'' -> '1019_20101217213900.mpg'
2010-12-21 14:34:18.848 ProgramInfo(): Updated pathname '':'' -> '1001_20101217212900.mpg'
2010-12-21 14:34:19.217 ProgramInfo(): Updated pathname '':'' -> '1001_20101217205900.mpg'
2010-12-21 14:34:19.408 ProgramInfo(): Updated pathname '':'' -> '1019_20101217205800.mpg'
2010-12-21 14:34:19.488 ProgramInfo(): Updated pathname '':'' -> '1001_20101217202800.mpg'
2010-12-21 14:34:19.731 ProgramInfo(): Updated pathname '':'' -> '1019_20101217191900.mpg'
2010-12-21 14:34:19.815 ProgramInfo(): Updated pathname '':'' -> '1019_20101217183800.mpg'
2010-12-21 14:34:20.202 ProgramInfo(): Updated pathname '':'' -> '1019_20101217151900.mpg'
2010-12-21 14:34:20.368 ProgramInfo(): Updated pathname '':'' -> '1019_20101217143800.mpg'
2010-12-21 14:34:20.433 ProgramInfo(): Updated pathname '':'' -> '1019_20101216235800.mpg'
2010-12-21 14:34:20.647 ProgramInfo(): Updated pathname '':'' -> '1007_20101216235400.mpg'
2010-12-21 14:34:20.681 ProgramInfo(): Updated pathname '':'' -> '1007_20101216232800.mpg'
2010-12-21 14:34:21.126 ProgramInfo(): Updated pathname '':'' -> '1019_20101216213900.mpg'
2010-12-21 14:34:21.234 ProgramInfo(): Updated pathname '':'' -> '1019_20101216205800.mpg'
2010-12-21 14:34:21.297 ProgramInfo(): Updated pathname '':'' -> '1019_20101216191801.mpg'
2010-12-21 14:34:21.486 ProgramInfo(): Updated pathname '':'' -> '1019_20101216190201.mpg'
2010-12-21 14:34:21.543 ProgramInfo(): Updated pathname '':'' -> '1019_20101216190200.mpg'
2010-12-21 14:34:21.584 ProgramInfo(1019_20101216190200.mpg), Error: GetPlaybackURL: '1019_20101216190200.mpg' should be local, but it can not be found.
2010-12-21 14:34:21.957 ProgramInfo(): Updated pathname '':'' -> '1019_20101216190100.mpg'
2010-12-21 14:34:21.998 ProgramInfo(1019_20101216190100.mpg), Error: GetPlaybackURL: '1019_20101216190100.mpg' should be local, but it can not be found.
2010-12-21 14:34:22.029 ProgramInfo(): Updated pathname '':'' -> '1007_20101216022800.mpg'
2010-12-21 14:34:22.162 ProgramInfo(): Updated pathname '':'' -> '1019_20101216003900.mpg'
2010-12-21 14:34:22.299 ProgramInfo(): Updated pathname '':'' -> '1007_20101215235800.mpg'
2010-12-21 14:34:22.463 ProgramInfo(): Updated pathname '':'' -> '1007_20101215223400.mpg'
2010-12-21 14:34:22.745 ProgramInfo(): Updated pathname '':'' -> '1007_20101215221300.mpg'
2010-12-21 14:34:22.747 ProgramInfo(): Updated pathname '':'' -> '1019_20101215215800.mpg'
2010-12-21 14:34:23.119 ProgramInfo(): Updated pathname '':'' -> '1019_20101215183800.mpg'
2010-12-21 14:34:23.234 ProgramInfo(): Updated pathname '':'' -> '1019_20101215151900.mpg'
2010-12-21 14:34:23.273 ProgramInfo(): Updated pathname '':'' -> '1019_20101215143800.mpg'
2010-12-21 14:34:23.575 ProgramInfo(): Updated pathname '':'' -> '1019_20101214235800.mpg'
2010-12-21 14:34:23.615 ProgramInfo(): Updated pathname '':'' -> '1007_20101214235400.mpg'
2010-12-21 14:34:23.943 ProgramInfo(): Updated pathname '':'' -> '1007_20101214232800.mpg'
2010-12-21 14:34:24.042 ProgramInfo(): Updated pathname '':'' -> '1019_20101214213800.mpg'
2010-12-21 14:34:24.147 ProgramInfo(): Updated pathname '':'' -> '1001_20101214195800.mpg'
2010-12-21 14:34:24.547 ProgramInfo(): Updated pathname '':'' -> '1019_20101214191800.mpg'
2010-12-21 14:34:24.576 ProgramInfo(): Updated pathname '':'' -> '1019_20101214183800.mpg'
2010-12-21 14:34:24.975 ProgramInfo(): Updated pathname '':'' -> '1019_20101214151900.mpg'
2010-12-21 14:34:25.015 ProgramInfo(): Updated pathname '':'' -> '1019_20101214143800.mpg'
2010-12-21 14:34:25.174 ProgramInfo(): Updated pathname '':'' -> '1004_20101214095300.mpg'
2010-12-21 14:34:25.436 ProgramInfo(): Updated pathname '':'' -> '1029_20101213233201.mpg'
2010-12-21 14:34:25.456 ProgramInfo(): Updated pathname '':'' -> '1028_20101213233201.mpg'
2010-12-21 14:34:25.622 ProgramInfo(1029_20101213233201.mpg), Error: GetPlaybackURL: '1029_20101213233201.mpg' should be local, but it can not be found.
2010-12-21 14:34:25.816 ProgramInfo(1028_20101213233201.mpg), Error: GetPlaybackURL: '1028_20101213233201.mpg' should be local, but it can not be found.
2010-12-21 14:34:25.824 ProgramInfo(): Updated pathname '':'' -> '1028_20101213233200.mpg'
2010-12-21 14:34:25.863 ProgramInfo(): Updated pathname '':'' -> '1019_20101213233100.mpg'
2010-12-21 14:34:26.036 ProgramInfo(1028_20101213233200.mpg), Error: GetPlaybackURL: '1028_20101213233200.mpg' should be local, but it can not be found.
2010-12-21 14:34:26.517 ProgramInfo(1019_20101213233100.mpg), Error: GetPlaybackURL: '1019_20101213233100.mpg' should be local, but it can not be found.
2010-12-21 14:34:26.520 ProgramInfo(): Updated pathname '':'' -> '1029_20101213233101.mpg'
2010-12-21 14:34:26.558 ProgramInfo(): Updated pathname '':'' -> '1028_20101213233101.mpg'
2010-12-21 14:34:26.619 ProgramInfo(1029_20101213233101.mpg), Error: GetPlaybackURL: '1029_20101213233101.mpg' should be local, but it can not be found.
2010-12-21 14:34:26.692 ProgramInfo(1028_20101213233101.mpg), Error: GetPlaybackURL: '1028_20101213233101.mpg' should be local, but it can not be found.
2010-12-21 14:34:26.694 ProgramInfo(): Updated pathname '':'' -> '1028_20101213233102.mpg'
2010-12-21 14:34:26.761 ProgramInfo(1028_20101213233102.mpg), Error: GetPlaybackURL: '1028_20101213233102.mpg' should be local, but it can not be found.
2010-12-21 14:34:27.153 ProgramInfo(): Updated pathname '':'' -> '1019_20101213151900.mpg'
2010-12-21 14:34:27.250 ProgramInfo(): Updated pathname '':'' -> '1019_20101213143800.mpg'
2010-12-21 14:34:27.438 ProgramInfo(): Updated pathname '':'' -> '1004_20101213102300.mpg'
2010-12-21 14:34:27.491 ProgramInfo(): Updated pathname '':'' -> '1001_20101213020800.mpg'
2010-12-21 14:34:27.571 ProgramInfo(): Updated pathname '':'' -> '1007_20101212222800.mpg'
2010-12-21 14:34:28.054 ProgramInfo(): Updated pathname '':'' -> '1019_20101212201800.mpg'
2010-12-21 14:34:28.147 ProgramInfo(): Updated pathname '':'' -> '1003_20101212192800.mpg'
2010-12-21 14:34:28.339 ProgramInfo(): Updated pathname '':'' -> '1001_20101212185800.mpg'
2010-12-21 14:34:28.388 ProgramInfo(): Updated pathname '':'' -> '1004_20101212113400.mpg'
2010-12-21 14:34:28.465 ProgramInfo(): Updated pathname '':'' -> '1003_20101212092800.mpg'
2010-12-21 14:34:29.033 ProgramInfo(): Updated pathname '':'' -> '1019_20101212013900.mpg'
2010-12-21 14:34:29.091 ProgramInfo(): Updated pathname '':'' -> '1019_20101212005900.mpg'
2010-12-21 14:34:29.235 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-12-21 14:34:29.322 ProgramInfo(): Updated pathname '':'' -> '1019_20101212001900.mpg'
2010-12-21 14:34:29.407 ProgramInfo(): Updated pathname '':'' -> '1019_20101211233800.mpg'
2010-12-21 14:34:29.534 ProgramInfo(): Updated pathname '':'' -> '1019_20101211221900.mpg'
2010-12-21 14:34:30.093 ProgramInfo(): Updated pathname '':'' -> '1019_20101211213900.mpg'
2010-12-21 14:34:30.209 ProgramInfo(): Updated pathname '':'' -> '1019_20101211205800.mpg'
2010-12-21 14:34:30.440 ProgramInfo(): Updated pathname '':'' -> '1019_20101211201800.mpg'
2010-12-21 14:34:30.451 ProgramInfo(): Updated pathname '':'' -> '1003_20101211185800.mpg'
2010-12-21 14:34:30.539 UPnpMedia: BuildMediaMap Done. Found 212 objects
2010-12-21 14:34:30.576 ProgramInfo(): Updated pathname '':'' -> '1001_20101211175800.mpg'
2010-12-21 14:34:31.060 ProgramInfo(): Updated pathname '':'' -> '1007_20101211001400.mpg'
2010-12-21 14:34:31.135 ProgramInfo(): Updated pathname '':'' -> '1007_20101210235400.mpg'
2010-12-21 14:34:31.307 ProgramInfo(): Updated pathname '':'' -> '1007_20101210232800.mpg'
2010-12-21 14:34:31.383 ProgramInfo(): Updated pathname '':'' -> '1007_20101210205800.mpg'
2010-12-21 14:34:31.505 ProgramInfo(): Updated pathname '':'' -> '1001_20101210205900.mpg'
2010-12-21 14:34:31.967 ProgramInfo(): Updated pathname '':'' -> '1001_20101210202800.mpg'
2010-12-21 14:34:32.013 ProgramInfo(): Updated pathname '':'' -> '1019_20101210191900.mpg'
2010-12-21 14:34:32.221 ProgramInfo(): Updated pathname '':'' -> '1019_20101210183800.mpg'
2010-12-21 14:34:32.270 ProgramInfo(): Updated pathname '':'' -> '1019_20101210151900.mpg'
2010-12-21 14:34:32.397 ProgramInfo(): Updated pathname '':'' -> '1019_20101210143800.mpg'
2010-12-21 14:34:32.845 ProgramInfo(): Updated pathname '':'' -> '1007_20101210004300.mpg'
2010-12-21 14:34:32.907 ProgramInfo(): Updated pathname '':'' -> '1019_20101210003800.mpg'
2010-12-21 14:34:33.172 ProgramInfo(): Updated pathname '':'' -> '1007_20101209222800.mpg'
2010-12-21 14:34:33.269 ProgramInfo(): Updated pathname '':'' -> '1019_20101209215800.mpg'
2010-12-21 14:34:33.332 ProgramInfo(): Updated pathname '':'' -> '1001_20101209212900.mpg'
2010-12-21 14:34:33.801 ProgramInfo(): Updated pathname '':'' -> '1001_20101209205800.mpg'
2010-12-21 14:34:33.882 ProgramInfo(): Updated pathname '':'' -> '1019_20101209191800.mpg'
2010-12-21 14:34:34.212 ProgramInfo(): Updated pathname '':'' -> '1019_20101209151800.mpg'
2010-12-21 14:34:34.245 ProgramInfo(): Updated pathname '':'' -> '1007_20101209024300.mpg'
2010-12-21 14:34:34.335 ProgramInfo(): Updated pathname '':'' -> '1007_20101209001300.mpg'
2010-12-21 14:34:34.824 ProgramInfo(): Updated pathname '':'' -> '1019_20101208235800.mpg'
2010-12-21 14:34:34.881 ProgramInfo(): Updated pathname '':'' -> '1019_20101208213900.mpg'
2010-12-21 14:34:35.142 ProgramInfo(): Updated pathname '':'' -> '1019_20101208205800.mpg'
2010-12-21 14:34:35.197 ProgramInfo(): Updated pathname '':'' -> '1019_20101208191900.mpg'
2010-12-21 14:34:35.294 ProgramInfo(): Updated pathname '':'' -> '1019_20101208183800.mpg'
2010-12-21 14:34:35.705 ProgramInfo(): Updated pathname '':'' -> '1019_20101208151900.mpg'
2010-12-21 14:34:35.756 ProgramInfo(): Updated pathname '':'' -> '1019_20101208143800.mpg'
2010-12-21 14:34:35.972 ProgramInfo(): Updated pathname '':'' -> '1029_20101208105300.mpg'
2010-12-21 14:34:35.989 ProgramInfo(): Updated pathname '':'' -> '1028_20101208095300.mpg'
2010-12-21 14:34:36.097 ProgramInfo(): Updated pathname '':'' -> '1029_20101208083300.mpg'
2010-12-21 14:34:36.489 ProgramInfo(): Updated pathname '':'' -> '1028_20101208073300.mpg'
2010-12-21 14:34:36.583 ProgramInfo(): Updated pathname '':'' -> '1019_20101208003800.mpg'
2010-12-21 14:34:36.820 ProgramInfo(): Updated pathname '':'' -> '1019_20101207215800.mpg'
2010-12-21 14:34:36.875 ProgramInfo(): Updated pathname '':'' -> '1001_20101207195800.mpg'
2010-12-21 14:34:36.920 ProgramInfo(): Updated pathname '':'' -> '1019_20101207191800.mpg'
2010-12-21 14:34:37.253 ProgramInfo(): Updated pathname '':'' -> '1019_20101207183800.mpg'
2010-12-21 14:34:37.391 ProgramInfo(): Updated pathname '':'' -> '1019_20101207151900.mpg'
2010-12-21 14:34:37.667 ProgramInfo(): Updated pathname '':'' -> '1019_20101207143800.mpg'
2010-12-21 14:34:37.723 ProgramInfo(): Updated pathname '':'' -> '1029_20101207104800.mpg'
2010-12-21 14:34:37.779 ProgramInfo(): Updated pathname '':'' -> '1028_20101207094800.mpg'
2010-12-21 14:34:38.156 ProgramInfo(): Updated pathname '':'' -> '1029_20101207083300.mpg'
2010-12-21 14:34:38.280 ProgramInfo(): Updated pathname '':'' -> '1028_20101207073300.mpg'
2010-12-21 14:34:38.514 ProgramInfo(): Updated pathname '':'' -> '1019_20101207003800.mpg'
2010-12-21 14:34:38.584 ProgramInfo(): Updated pathname '':'' -> '1019_20101206215800.mpg'
2010-12-21 14:34:38.684 ProgramInfo(): Updated pathname '':'' -> '1019_20101206191900.mpg'
2010-12-21 14:34:39.151 ProgramInfo(): Updated pathname '':'' -> '1019_20101206183800.mpg'
2010-12-21 14:34:39.246 ProgramInfo(): Updated pathname '':'' -> '1019_20101206151900.mpg'
2010-12-21 14:34:39.452 ProgramInfo(): Updated pathname '':'' -> '1019_20101206143800.mpg'
2010-12-21 14:34:39.479 ProgramInfo(): Updated pathname '':'' -> '1001_20101206011800.mpg'
2010-12-21 14:34:39.564 ProgramInfo(): Updated pathname '':'' -> '1007_20101205221900.mpg'
2010-12-21 14:34:39.975 ProgramInfo(): Updated pathname '':'' -> '1007_20101205215800.mpg'
2010-12-21 14:34:40.059 ProgramInfo(): Updated pathname '':'' -> '1019_20101205201800.mpg'
2010-12-21 14:34:40.342 ProgramInfo(): Updated pathname '':'' -> '1003_20101205195800.mpg'
2010-12-21 14:34:40.364 ProgramInfo(): Updated pathname '':'' -> '1001_20101205192800.mpg'
2010-12-21 14:34:40.449 ProgramInfo(): Updated pathname '':'' -> '1019_20101205141900.mpg'
2010-12-21 14:34:40.876 ProgramInfo(): Updated pathname '':'' -> '1019_20101205133800.mpg'
2010-12-21 14:34:40.963 ProgramInfo(): Updated pathname '':'' -> '1003_20101205094300.mpg'
2010-12-21 14:34:41.240 ProgramInfo(): Updated pathname '':'' -> '1007_20101204233300.mpg'
2010-12-21 14:34:41.276 ProgramInfo(): Updated pathname '':'' -> '1028_20101204205400.mpg'
2010-12-21 14:34:41.356 ProgramInfo(): Updated pathname '':'' -> '1029_20101204204800.mpg'
2010-12-21 14:34:41.796 ProgramInfo(): Updated pathname '':'' -> '1028_20101204202200.mpg'
2010-12-21 14:34:41.929 ProgramInfo(): Updated pathname '':'' -> '1019_20101204202201.mpg'
2010-12-21 14:34:41.965 ProgramInfo(1019_20101204202201.mpg), Error: GetPlaybackURL: '1019_20101204202201.mpg' should be local, but it can not be found.
2010-12-21 14:34:42.144 ProgramInfo(): Updated pathname '':'' -> '1003_20101204202100.mpg'
2010-12-21 14:34:42.183 ProgramInfo(1003_20101204202100.mpg), Error: GetPlaybackURL: '1003_20101204202100.mpg' should be local, but it can not be found.
2010-12-21 14:34:42.202 ProgramInfo(): Updated pathname '':'' -> '1001_20101204202101.mpg'
2010-12-21 14:34:42.250 ProgramInfo(1001_20101204202101.mpg), Error: GetPlaybackURL: '1001_20101204202101.mpg' should be local, but it can not be found.
2010-12-21 14:34:42.255 ProgramInfo(): Updated pathname '':'' -> '1028_20101204202101.mpg'
2010-12-21 14:34:42.317 ProgramInfo(1028_20101204202101.mpg), Error: GetPlaybackURL: '1028_20101204202101.mpg' should be local, but it can not be found.
2010-12-21 14:34:42.658 ProgramInfo(): Updated pathname '':'' -> '1019_20101204202100.mpg'
2010-12-21 14:34:42.693 ProgramInfo(1019_20101204202100.mpg), Error: GetPlaybackURL: '1019_20101204202100.mpg' should be local, but it can not be found.
2010-12-21 14:34:42.755 ProgramInfo(): Updated pathname '':'' -> '1019_20101204001800.mpg'
2010-12-21 14:34:42.943 ProgramInfo(): Updated pathname '':'' -> '1007_20101204001400.mpg'
2010-12-21 14:34:43.015 ProgramInfo(): Updated pathname '':'' -> '1007_20101203234900.mpg'
2010-12-21 14:34:43.106 ProgramInfo(): Updated pathname '':'' -> '1007_20101203232900.mpg'
2010-12-21 14:34:43.476 ProgramInfo(): Updated pathname '':'' -> '1019_20101203223900.mpg'
2010-12-21 14:34:43.607 ProgramInfo(): Updated pathname '':'' -> '1019_20101203215800.mpg'
2010-12-21 14:34:43.823 ProgramInfo(): Updated pathname '':'' -> '1007_20101203205900.mpg'
2010-12-21 14:34:43.839 ProgramInfo(): Updated pathname '':'' -> '1001_20101203202800.mpg'
2010-12-21 14:34:43.947 ProgramInfo(): Updated pathname '':'' -> '1019_20101203191800.mpg'
2010-12-21 14:34:44.430 ProgramInfo(): Updated pathname '':'' -> '1028_20101203172900.mpg'
2010-12-21 14:34:44.559 ProgramInfo(): Updated pathname '':'' -> '1028_20101203165800.mpg'
2010-12-21 14:34:44.835 ProgramInfo(): Updated pathname '':'' -> '1019_20101203151900.mpg'
2010-12-21 14:34:44.848 ProgramInfo(): Updated pathname '':'' -> '1019_20101203143800.mpg'
2010-12-21 14:34:44.966 ProgramInfo(): Updated pathname '':'' -> '1007_20101203011300.mpg'
2010-12-21 14:34:45.407 ProgramInfo(): Updated pathname '':'' -> '1019_20101203005900.mpg'
2010-12-21 14:34:45.563 ProgramInfo(): Updated pathname '':'' -> '1019_20101203001800.mpg'
2010-12-21 14:34:45.712 ProgramInfo(): Updated pathname '':'' -> '1007_20101202231900.mpg'
2010-12-21 14:34:45.807 ProgramInfo(): Updated pathname '':'' -> '1007_20101202225900.mpg'
2010-12-21 14:34:45.819 ProgramInfo(): Updated pathname '':'' -> '1019_20101202223900.mpg'
2010-12-21 14:34:45.919 ProgramInfo(): Updated pathname '':'' -> '1007_20101202222800.mpg'
2010-12-21 14:34:46.335 ProgramInfo(): Updated pathname '':'' -> '1019_20101202215800.mpg'
2010-12-21 14:34:46.726 ProgramInfo(): Updated pathname '':'' -> '1001_20101202205800.mpg'
2010-12-21 14:34:46.730 ProgramInfo(): Updated pathname '':'' -> '1001_20101202212900.mpg'
2010-12-21 14:34:46.844 ProgramInfo(): Updated pathname '':'' -> '1019_20101202194900.mpg'
2010-12-21 14:34:46.872 ProgramInfo(): Updated pathname '':'' -> '1019_20101202190800.mpg'
2010-12-21 14:34:46.968 ProgramInfo(): Updated pathname '':'' -> '1028_20101202165900.mpg'
2010-12-21 14:34:47.240 ProgramInfo(): Updated pathname '':'' -> '1028_20101202162300.mpg'
2010-12-21 14:34:47.627 ProgramInfo(): Updated pathname '':'' -> '1019_20101202151900.mpg'
2010-12-21 14:34:47.650 ProgramInfo(): Updated pathname '':'' -> '1019_20101202143800.mpg'
2010-12-21 14:34:47.746 ProgramInfo(): Updated pathname '':'' -> '1007_20101202035300.mpg'
2010-12-21 14:34:47.799 ProgramInfo(): Updated pathname '':'' -> '1007_20101202002900.mpg'
2010-12-21 14:34:47.904 ProgramInfo(): Updated pathname '':'' -> '1019_20101201233900.mpg'
2010-12-21 14:34:48.199 ProgramInfo(): Updated pathname '':'' -> '1007_20101201230900.mpg'
2010-12-21 14:34:48.512 ProgramInfo(): Updated pathname '':'' -> '1007_20101201224300.mpg'
2010-12-21 14:34:48.551 ProgramInfo(): Updated pathname '':'' -> '1019_20101201213900.mpg'
2010-12-21 14:34:48.617 ProgramInfo(): Updated pathname '':'' -> '1019_20101201205800.mpg'
2010-12-21 14:34:48.662 ProgramInfo(): Updated pathname '':'' -> '1019_20101201191800.mpg'
2010-12-21 14:34:48.773 ProgramInfo(): Updated pathname '':'' -> '1028_20101201165900.mpg'
2010-12-21 14:34:49.028 ProgramInfo(): Updated pathname '':'' -> '1028_20101201162800.mpg'
2010-12-21 14:34:49.440 ProgramInfo(): Updated pathname '':'' -> '1019_20101201151800.mpg'
2010-12-21 14:34:49.508 ProgramInfo(): Updated pathname '':'' -> '1019_20101201005900.mpg'
2010-12-21 14:34:49.601 ProgramInfo(): Updated pathname '':'' -> '1019_20101201001900.mpg'
2010-12-21 14:34:49.674 ProgramInfo(): Updated pathname '':'' -> '1007_20101130234900.mpg'
2010-12-21 14:34:49.834 ProgramInfo(): Updated pathname '':'' -> '1007_20101130232900.mpg'
2010-12-21 14:34:50.042 ProgramInfo(): Updated pathname '':'' -> '1019_20101130223900.mpg'
2010-12-21 14:34:50.397 ProgramInfo(): Updated pathname '':'' -> '1019_20101130215800.mpg'
2010-12-21 14:34:50.430 ProgramInfo(): Updated pathname '':'' -> '1001_20101130195800.mpg'
2010-12-21 14:34:50.518 ProgramInfo(): Updated pathname '':'' -> '1019_20101130191800.mpg'
2010-12-21 14:34:50.572 ProgramInfo(): Updated pathname '':'' -> '1019_20101130175800.mpg'
2010-12-21 14:34:50.717 ProgramInfo(): Updated pathname '':'' -> '1019_20101130151900.mpg'
2010-12-21 14:34:50.915 ProgramInfo(): Updated pathname '':'' -> '1019_20101130143900.mpg'
2010-12-21 14:34:51.245 ProgramInfo(): Updated pathname '':'' -> '1019_20101130135800.mpg'
2010-12-21 14:34:51.277 ProgramInfo(): Updated pathname '':'' -> '1028_20101130094800.mpg'
2010-12-21 14:34:51.387 ProgramInfo(): Updated pathname '':'' -> '1019_20101130005900.mpg'
2010-12-21 14:34:51.427 ProgramInfo(): Updated pathname '':'' -> '1019_20101130001800.mpg'
2010-12-21 14:34:51.617 ProgramInfo(): Updated pathname '':'' -> '1019_20101129223900.mpg'
2010-12-21 14:34:51.827 ProgramInfo(): Updated pathname '':'' -> '1019_20101129215800.mpg'
2010-12-21 14:34:52.212 ProgramInfo(): Updated pathname '':'' -> '1019_20101123061702.mpg'
2010-12-21 14:34:52.223 ProgramInfo(): Updated pathname '':'' -> '1019_20101129191900.mpg'
2010-12-21 14:34:52.250 ProgramInfo(1019_20101123061702.mpg), Error: GetPlaybackURL: '1019_20101123061702.mpg' should be local, but it can not be found.
2010-12-21 14:34:52.344 ProgramInfo(): Updated pathname '':'' -> '1019_20101123061701.mpg'
2010-12-21 14:34:52.386 ProgramInfo(1019_20101123061701.mpg), Error: GetPlaybackURL: '1019_20101123061701.mpg' should be local, but it can not be found.
2010-12-21 14:34:52.408 ProgramInfo(): Updated pathname '':'' -> '1002_20101122185900.mpg'
2010-12-21 14:34:52.462 ProgramInfo(1002_20101122185900.mpg), Error: GetPlaybackURL: '1002_20101122185900.mpg' should be local, but it can not be found.
2010-12-21 14:34:52.569 ProgramInfo(): Updated pathname '':'' -> '1019_20101122185900.mpg'
2010-12-21 14:34:52.612 ProgramInfo(1019_20101122185900.mpg), Error: GetPlaybackURL: '1019_20101122185900.mpg' should be local, but it can not be found.
2010-12-21 14:34:52.713 ProgramInfo(): Updated pathname '':'' -> '1028_20101122185902.mpg'
2010-12-21 14:34:52.746 ProgramInfo(1028_20101122185902.mpg), Error: GetPlaybackURL: '1028_20101122185902.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.102 ProgramInfo(): Updated pathname '':'' -> '1028_20101122185901.mpg'
2010-12-21 14:34:53.138 ProgramInfo(1028_20101122185901.mpg), Error: GetPlaybackURL: '1028_20101122185901.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.146 ProgramInfo(): Updated pathname '':'' -> '1019_20101122185902.mpg'
2010-12-21 14:34:53.205 ProgramInfo(1019_20101122185902.mpg), Error: GetPlaybackURL: '1019_20101122185902.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.182 ProgramInfo(): Updated pathname '':'' -> '1019_20101122185901.mpg'
2010-12-21 14:34:53.245 ProgramInfo(): Updated pathname '':'' -> '1019_20101121123800.mpg'
2010-12-21 14:34:53.274 ProgramInfo(1019_20101122185901.mpg), Error: GetPlaybackURL: '1019_20101122185901.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.346 ProgramInfo(1019_20101121123800.mpg), Error: GetPlaybackURL: '1019_20101121123800.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.355 ProgramInfo(): Updated pathname '':'' -> '1001_20101115091200.mpg'
2010-12-21 14:34:53.417 ProgramInfo(1001_20101115091200.mpg), Error: GetPlaybackURL: '1001_20101115091200.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.494 ProgramInfo(): Updated pathname '':'' -> '1019_20101113161501.mpg'
2010-12-21 14:34:53.535 ProgramInfo(1019_20101113161501.mpg), Error: GetPlaybackURL: '1019_20101113161501.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.862 ProgramInfo(): Updated pathname '':'' -> '1019_20101113161500.mpg'
2010-12-21 14:34:53.900 ProgramInfo(1019_20101113161500.mpg), Error: GetPlaybackURL: '1019_20101113161500.mpg' should be local, but it can not be found.
2010-12-21 14:34:53.936 ProgramInfo(): Updated pathname '':'' -> '1019_20101112045800.mpg'
2010-12-21 14:34:53.985 ProgramInfo(1019_20101112045800.mpg), Error: GetPlaybackURL: '1019_20101112045800.mpg' should be local, but it can not be found.
2010-12-21 14:34:54.103 ProgramInfo(): Updated pathname '':'' -> '1019_20101111213900.mpg'
2010-12-21 14:34:54.128 ProgramInfo(): Updated pathname '':'' -> '1001_20101108041200.mpg'
2010-12-21 14:34:54.144 ProgramInfo(1019_20101111213900.mpg), Error: GetPlaybackURL: '1019_20101111213900.mpg' should be local, but it can not be found.
2010-12-21 14:34:54.228 ProgramInfo(1001_20101108041200.mpg), Error: GetPlaybackURL: '1001_20101108041200.mpg' should be local, but it can not be found.
2010-12-21 14:34:54.230 ProgramInfo(): Updated pathname '':'' -> '1019_20101108041202.mpg'
2010-12-21 14:34:54.297 ProgramInfo(1019_20101108041202.mpg), Error: GetPlaybackURL: '1019_20101108041202.mpg' should be local, but it can not be found.
2010-12-21 14:34:54.314 ProgramInfo(): Updated pathname '':'' -> '1019_20101108041200.mpg'
2010-12-21 14:34:54.365 ProgramInfo(1019_20101108041200.mpg), Error: GetPlaybackURL: '1019_20101108041200.mpg' should be local, but it can not be found.
2010-12-21 14:34:54.791 ProgramInfo(): Updated pathname '':'' -> '1007_20101108041200.mpg'
2010-12-21 14:34:54.832 ProgramInfo(1007_20101108041200.mpg), Error: GetPlaybackURL: '1007_20101108041200.mpg' should be local, but it can not be found.
2010-12-21 14:34:54.861 ProgramInfo(): Updated pathname '':'' -> '1003_20101108041100.mpg'
2010-12-21 14:34:54.907 ProgramInfo(1003_20101108041100.mpg), Error: GetPlaybackURL: '1003_20101108041100.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.090 ProgramInfo(): Updated pathname '':'' -> '1019_20101102230900.mpg'
2010-12-21 14:34:55.105 ProgramInfo(): Updated pathname '':'' -> '1001_20101102230901.mpg'
2010-12-21 14:34:55.133 ProgramInfo(1019_20101102230900.mpg), Error: GetPlaybackURL: '1019_20101102230900.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.217 ProgramInfo(1001_20101102230901.mpg), Error: GetPlaybackURL: '1001_20101102230901.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.219 ProgramInfo(): Updated pathname '':'' -> '1028_20101102230801.mpg'
2010-12-21 14:34:55.273 ProgramInfo(): Updated pathname '':'' -> '1028_20101102230802.mpg'
2010-12-21 14:34:55.301 ProgramInfo(1028_20101102230801.mpg), Error: GetPlaybackURL: '1028_20101102230801.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.374 ProgramInfo(1028_20101102230802.mpg), Error: GetPlaybackURL: '1028_20101102230802.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.638 ProgramInfo(): Updated pathname '':'' -> '1028_20101101190302.mpg'
2010-12-21 14:34:55.676 ProgramInfo(1028_20101101190302.mpg), Error: GetPlaybackURL: '1028_20101101190302.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.683 ProgramInfo(): Updated pathname '':'' -> '1028_20101101190301.mpg'
2010-12-21 14:34:55.777 ProgramInfo(1028_20101101190301.mpg), Error: GetPlaybackURL: '1028_20101101190301.mpg' should be local, but it can not be found.
2010-12-21 14:34:55.980 ProgramInfo(): Updated pathname '':'' -> '1028_20101020202800.mpg'
2010-12-21 14:34:56.011 ProgramInfo(1028_20101020202800.mpg), Error: GetPlaybackURL: '1028_20101020202800.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.090 ProgramInfo(): Updated pathname '':'' -> '1028_20101020201300.mpg'
2010-12-21 14:34:56.120 ProgramInfo(1028_20101020201300.mpg), Error: GetPlaybackURL: '1028_20101020201300.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.190 ProgramInfo(): Updated pathname '':'' -> '1003_20101020210857.mpg'
2010-12-21 14:34:56.237 ProgramInfo(): Updated pathname '':'' -> '1003_20101020210910.mpg'
2010-12-21 14:34:56.239 ProgramInfo(1003_20101020210857.mpg), Error: GetPlaybackURL: '1003_20101020210857.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.316 ProgramInfo(1003_20101020210910.mpg), Error: GetPlaybackURL: '1003_20101020210910.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.490 ProgramInfo(): Updated pathname '':'' -> '1019_20100723005900.mpg'
2010-12-21 14:34:56.524 ProgramInfo(1019_20100723005900.mpg), Error: GetPlaybackURL: '1019_20100723005900.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.548 ProgramInfo(): Updated pathname '':'' -> '1019_20100723001900.mpg'
2010-12-21 14:34:56.600 ProgramInfo(1019_20100723001900.mpg), Error: GetPlaybackURL: '1019_20100723001900.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.730 ProgramInfo(): Updated pathname '':'' -> '1019_20100722233900.mpg'
2010-12-21 14:34:56.769 ProgramInfo(1019_20100722233900.mpg), Error: GetPlaybackURL: '1019_20100722233900.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.802 ProgramInfo(): Updated pathname '':'' -> '1007_20100722232400.mpg'
2010-12-21 14:34:56.850 ProgramInfo(1007_20100722232400.mpg), Error: GetPlaybackURL: '1007_20100722232400.mpg' should be local, but it can not be found.
2010-12-21 14:34:56.982 ProgramInfo(): Updated pathname '':'' -> '1007_20100722225800.mpg'
2010-12-21 14:34:57.017 ProgramInfo(): Updated pathname '':'' -> '1019_20100722225900.mpg'
2010-12-21 14:34:57.033 ProgramInfo(1007_20100722225800.mpg), Error: GetPlaybackURL: '1007_20100722225800.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.112 ProgramInfo(1019_20100722225900.mpg), Error: GetPlaybackURL: '1019_20100722225900.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.256 ProgramInfo(): Updated pathname '':'' -> '1019_20100722221900.mpg'
2010-12-21 14:34:57.333 ProgramInfo(): Updated pathname '':'' -> '1019_20100722214400.mpg'
2010-12-21 14:34:57.361 ProgramInfo(1019_20100722221900.mpg), Error: GetPlaybackURL: '1019_20100722221900.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.440 ProgramInfo(1019_20100722214400.mpg), Error: GetPlaybackURL: '1019_20100722214400.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.443 ProgramInfo(): Updated pathname '':'' -> '1019_20100722213900.mpg'
2010-12-21 14:34:57.487 ProgramInfo(): Updated pathname '':'' -> '1019_20100722205800.mpg'
2010-12-21 14:34:57.512 ProgramInfo(1019_20100722213900.mpg), Error: GetPlaybackURL: '1019_20100722213900.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.597 ProgramInfo(1019_20100722205800.mpg), Error: GetPlaybackURL: '1019_20100722205800.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.694 ProgramInfo(): Updated pathname '':'' -> '1003_20100722122900.mpg'
2010-12-21 14:34:57.731 ProgramInfo(1003_20100722122900.mpg), Error: GetPlaybackURL: '1003_20100722122900.mpg' should be local, but it can not be found.
2010-12-21 14:34:57.968 ProgramInfo(): Updated pathname '':'' -> '1003_20100722112900.mpg'
2010-12-21 14:34:58.006 ProgramInfo(1003_20100722112900.mpg), Error: GetPlaybackURL: '1003_20100722112900.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.161 ProgramInfo(): Updated pathname '':'' -> '1003_20100722102800.mpg'
2010-12-21 14:34:58.200 ProgramInfo(1003_20100722102800.mpg), Error: GetPlaybackURL: '1003_20100722102800.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.233 ProgramInfo(): Updated pathname '':'' -> '1028_20100722072800.mpg'
2010-12-21 14:34:58.275 ProgramInfo(1028_20100722072800.mpg), Error: GetPlaybackURL: '1028_20100722072800.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.319 ProgramInfo(): Updated pathname '':'' -> '1019_20100722001800.mpg'
2010-12-21 14:34:58.351 ProgramInfo(): Updated pathname '':'' -> '1007_20100721231900.mpg'
2010-12-21 14:34:58.360 ProgramInfo(1019_20100722001800.mpg), Error: GetPlaybackURL: '1019_20100722001800.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.455 ProgramInfo(): Updated pathname '':'' -> '1007_20100721225800.mpg'
2010-12-21 14:34:58.456 ProgramInfo(1007_20100721231900.mpg), Error: GetPlaybackURL: '1007_20100721231900.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.526 ProgramInfo(1007_20100721225800.mpg), Error: GetPlaybackURL: '1007_20100721225800.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.675 ProgramInfo(): Updated pathname '':'' -> '1019_20100721213900.mpg'
2010-12-21 14:34:58.713 ProgramInfo(1019_20100721213900.mpg), Error: GetPlaybackURL: '1019_20100721213900.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.878 ProgramInfo(): Updated pathname '':'' -> '1019_20100721205800.mpg'
2010-12-21 14:34:58.912 ProgramInfo(1019_20100721205800.mpg), Error: GetPlaybackURL: '1019_20100721205800.mpg' should be local, but it can not be found.
2010-12-21 14:34:58.982 ProgramInfo(): Updated pathname '':'' -> '1003_20100721122900.mpg'
2010-12-21 14:34:59.021 ProgramInfo(1003_20100721122900.mpg), Error: GetPlaybackURL: '1003_20100721122900.mpg' should be local, but it can not be found.
2010-12-21 14:34:59.202 ProgramInfo(): Updated pathname '':'' -> '1003_20100721112900.mpg'
2010-12-21 14:34:59.328 ProgramInfo(): Updated pathname '':'' -> '1003_20100721102800.mpg'
2010-12-21 14:34:59.439 ProgramInfo(1003_20100721112900.mpg), Error: GetPlaybackURL: '1003_20100721112900.mpg' should be local, but it can not be found.
2010-12-21 14:34:59.516 ProgramInfo(): Updated pathname '':'' -> '1028_20100721072800.mpg'
2010-12-21 14:34:59.518 ProgramInfo(1003_20100721102800.mpg), Error: GetPlaybackURL: '1003_20100721102800.mpg' should be local, but it can not be found.
2010-12-21 14:34:59.597 ProgramInfo(1028_20100721072800.mpg), Error: GetPlaybackURL: '1028_20100721072800.mpg' should be local, but it can not be found.
2010-12-21 14:34:59.599 ProgramInfo(): Updated pathname '':'' -> '1007_20100720234900.mpg'
2010-12-21 14:34:59.666 ProgramInfo(1007_20100720234900.mpg), Error: GetPlaybackURL: '1007_20100720234900.mpg' should be local, but it can not be found.
2010-12-21 14:34:59.691 ProgramInfo(): Updated pathname '':'' -> '1007_20100720232800.mpg'
2010-12-21 14:34:59.742 ProgramInfo(1007_20100720232800.mpg), Error: GetPlaybackURL: '1007_20100720232800.mpg' should be local, but it can not be found.
2010-12-21 14:34:59.772 ProgramInfo(): Updated pathname '':'' -> '1019_20100720205800.mpg'
2010-12-21 14:34:59.818 ProgramInfo(1019_20100720205800.mpg), Error: GetPlaybackURL: '1019_20100720205800.mpg' should be local, but it can not be found.
2010-12-21 14:35:00.302 ProgramInfo(): Updated pathname '':'' -> '1019_20100720042108.mpg'
2010-12-21 14:35:00.344 ProgramInfo(1019_20100720042108.mpg), Error: GetPlaybackURL: '1019_20100720042108.mpg' should be local, but it can not be found.
2010-12-21 14:35:00.374 ProgramInfo(): Updated pathname '':'' -> '1019_20100720042106.mpg'
2010-12-21 14:35:00.420 ProgramInfo(1019_20100720042106.mpg), Error: GetPlaybackURL: '1019_20100720042106.mpg' should be local, but it can not be found.
2010-12-21 14:35:00.425 ProgramInfo(): Updated pathname '':'' -> '1019_20100720042105.mpg'
2010-12-21 14:35:00.464 ProgramInfo(): Updated pathname '':'' -> '1019_20100720042104.mpg'
2010-12-21 14:35:00.487 ProgramInfo(1019_20100720042105.mpg), Error: GetPlaybackURL: '1019_20100720042105.mpg' should be local, but it can not be found.
2010-12-21 14:35:00.563 ProgramInfo(1019_20100720042104.mpg), Error: GetPlaybackURL: '1019_20100720042104.mpg' should be local, but it can not be found.
2010-12-21 14:35:00.565 ProgramInfo(): Updated pathname '':'' -> '1019_20100720042103.mpg'

---

### Post by thatguruguy on 2010-12-21
1. Are you able to watch live tv?
2. Make sure your server settings are correct.
3. Are you using myth .23 or .24? Are your storage groups set up correctly?

---

### Post by tonycollinet on 2010-12-21
Checked live TV, and was working, but not reliable on one of the tuners. I've fiddled with the antenna wiring, and it seems to be back again now. Let's see.

---

### Post by thatguruguy on 2010-12-21
There's a very real possibility that the tuner problem caused the recording problem.

---

