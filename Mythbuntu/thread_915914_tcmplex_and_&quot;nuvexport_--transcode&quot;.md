---
title: "tcmplex and &quot;nuvexport --transcode&quot;?"
date: 2008-09-10
forum: Mythbuntu
---

### Post by klc5555 on 2008-09-10
On Mythbuntu 7.10 with Myth 0.20.2. I installed nuvexport (0.4, 0.5   is evidently incompatible with 0.20.2) in order to use it as a workaround for cutlisting dvb recordings where mythtranscode fails with the known error 247 "expectedPTS != expectedDTS+ptsIncrement", which is still an open bug I believe in Myth 0.21

I can use "nuvexport --transcode" to trim cutlisted .mpg's and turn them into .avi files. But nearly all options under "nuvexport --transcode" require tcmplex, which is not included in this particular version of the transcode tools, nor in nuvexport 0.4x

The Hardy repositories list nuvexport as being returned to the distribution (but not in Gutsy or backports). Does anyone know whether this version of nuvexport (and its associated transcode tools) include some version of the no-longer-maintained tcmplex (or the rewritten version tcplex-panteltje)? Can Hardy's version of nuvexport run the full range of options listed under "nuvexport --transcode"? 

Or does anyone know how to properly install the *.tgz tarball for tcmplex-panteltje onto a Gutsy machine?

Cheers! :)

---

