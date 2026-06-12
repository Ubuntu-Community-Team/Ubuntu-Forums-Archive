---
title: "ImageMagick 7.x: Shell script not working"
date: 2020-07-25
forum: Multimedia Software
---

### Post by claus on 2020-07-25
Hi,

I made a shell script [FONT=Courier New]gradient.sh[/FONT] containing one of the [examples]("http://www.imagemagick.org/Usage/canvas/#sparse_fill") from the IM site

```

#!bin/sh

magick sparse_source.gif txt:- |\
    sed '1d; / 0) /d; s/:.* /,/;' |\
      convert sparse_source.gif -alpha off \
              -sparse-color shepards '@-' sparse_fill.png

```

but when I try to run the script with [FONT=Courier New]gradient.sh[/FONT], I get

```

gradient.sh: command not found

```

although I made the script executable with [FONT=Courier New]chmod +x gradient.sh[/FONT]. Wehn I invoke the script with [FONT=Courier New]sh gradient.sh[/FONT], I get numerous error messages:

```

convert-im6.q16: attempt to perform an operation not allowed by the security policy `@-' @ error/property.c/InterpretImageProperties/3666.
convert-im6.q16: memory allocation failed SparseColorOption @ error/mogrify.c/SparseColorOption/535.
convert-im6.q16: attempt to perform an operation not allowed by the security policy `@-' @ error/property.c/InterpretImageProperties/3666.

```

Is anyone familiar with IM and can help me?

TIA,

Claus

---

