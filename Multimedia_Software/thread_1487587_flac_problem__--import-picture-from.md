---
title: "flac problem:  --import-picture-from"
date: 2010-05-19
forum: Multimedia Software
---

### Post by WDYSUN on 2010-05-19
Dear All,

i wrote this script to embed the cover.jpg as a metadata content of a list of flac files:

```

for f in `find  -name '*.flac'`
    do metaflac --import-picture-from=cover.jpg  $f
done

```

now when I run this script in on flacs I have two different situations:


1. I successfully embed the cover.jpg in the flac even though the temrinal gives me the following errors

```

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.
All: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.
of: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

etc. etc.

```

2. the terminal gives me the same output but I do not embed any picture.

Can somebody tell me why this is the case?

Cheers
Pietro

---

