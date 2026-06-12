---
title: "FFMPEG keep the original timestamp i.e. Date Modified/Date Created/Date?"
date: 2012-07-16
forum: Multimedia Software
---

### Post by darlyn on 2012-07-16
Converting some vids, need to keep the original Date Modified/Date Created/Date data. How?

---

### Post by beandog on 2012-07-17
> **darlyn said:**
> Converting some vids, need to keep the original Date Modified/Date Created/Date data. How?

Check the manpage and look for metadata.  I believe it should copy it by default, but maybe not.

> -map_metadata outfile[,metadata]:infile[,metadata]
           Set metadata information of outfile from infile. Note that those
           are file indices (zero-based), not filenames.  Optional metadata
           parameters specify, which metadata to copy - (g)lobal (i.e.
           metadata that applies to the whole file), per-(s)tream,
           per-(c)hapter or per-(p)rogram. All metadata specifiers other than
           global must be followed by the stream/chapter/program number. If
           metadata specifier is omitted, it defaults to global.

           By default, global metadata is copied from the first input file to
           all output files, per-stream and per-chapter metadata is copied
           along with streams/chapters. These default mappings are disabled by
           creating any mapping of the relevant type. A negative file index
           can be used to create a dummy mapping that just disables automatic
           copying.

           For example to copy metadata from the first stream of the input
           file to global metadata of the output file:

                   ffmpeg -i in.ogg -map_metadata 0:0,s0 out.mp3


---

