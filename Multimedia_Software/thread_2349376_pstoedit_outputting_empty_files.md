---
title: "pstoedit outputting empty files"
date: 2017-01-13
forum: Multimedia Software
---

### Post by nickTaylor1181 on 2017-01-13
Hi all.


I'm back into the never-ending quest to get non-straight-line-segment DXFs out of Inkscape... Have tried various things...  am now attempting pstoedit.


I've tried various permutations, of the line below, and no matter what I do (or what I inpuput), it outputs and empty dxf file

So

```
pstoedit -dt -f -v dxf:-polyaslines\ -mm infile.eps outfile.dxf
```


outputs:

```
  0SECTION
  2
HEADER
  9
$ACADVER
  1
AC1009
  9
$EXTMIN
 10
0.0
 20
0.0
 30
0.0
  9
$EXTMAX
 10
1000.0
 20
1000.0
 30
0.0
  9
$FILLMODE
 70
 0
  9
$SPLFRAME
 70
 1
  0
ENDSEC
  0
SECTION
  2
TABLES
  0
TABLE
  2
LAYER
 70
1
  0
LAYER
  2
0
 70
     0
 62
     7
  6
CONTINUOUS
  0
ENDTAB
  0
ENDSEC
  0
SECTION
  2
ENTITIES
  0
ENDSEC
  0
EOF
```


Any idea what I'm missing?


......................................................................................................................................................................................................

I'm using ubuntu studio 16.04 

and 

pstoedit: version 3.70 / DLL interface 108 (built: Mar 13 2016 - release build - g++ 5.3.1 20160311 - 64-bit)

---

### Post by nickTaylor1181 on 2017-01-15
Ah - it was a draftsight rendering issue.


```
View > Rebuild All
```

Fixes it.

---

