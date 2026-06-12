---
title: "No kivio?"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2010-09-12
Does anyone know why "kivio" isn't available in the 10.10 repositories?
 
I've installed the "koffice" package, and that doesn't provide it.
 
I've tried installing the "kivio" package, but that seems to not exist.
 
I've used "apt-file search kivio", but that doesn't turn up any packages with a kivio binary.

---

### Post by 23meg on 2010-09-12
Looks like it was dropped [in Debian]("http://packages.debian.org/changelogs/pool/main/k/koffice/koffice_2.2.1-2/changelog"), and upstream:

>  koffice  (1:1.9.98.0-1) experimental; urgency=low

   * New upstream release, first beta.
   * Drop Kivio, KFormula and Kexi, they won't be released in future koffice 2.0.
   * Remove build depends on: freeglut3-dev, libglpk-dev,
     libgraphicsmagick++1-dev, libpqxx-dev and python-dev.
   * Add build depend on libkdcraw5-dev.
   * Drop patch embed_eigen_in_koffice2_alpha10.diff and
     build depend on libeigen2-dev.
   * Add debug package: koffice-dbg.
   * Update install files.
   * Update to debhelper compatibility 7.
   * Remove Suggests: koffice-i18n, still no translations available.
   * Rework in *.install files and use some wildcards instead.

 -- Ana Beatriz Guerrero Lopez <ana@debian.org>  Thu, 25 Sep 2008 07:53:31 +0200 

---

### Post by christian.convey on 2010-09-12
> **23meg said:**
> Looks like it was dropped [in Debian]("http://packages.debian.org/changelogs/pool/main/k/koffice/koffice_2.2.1-2/changelog"), and upstream:
 
Shoot. Apparently it's lacking a maintainer. Thanks for the info.

---

