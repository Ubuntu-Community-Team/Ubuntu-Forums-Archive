---
title: "OT: How it the repository created?"
date: 2009-03-17
forum: Mythbuntu
---

### Post by jyavenard on 2009-03-17
Hi

I am trying to create a packages repository similar to the mythbuntu repository.
It would provide packages for both Hardy and Intrepid.

I see that the mythbuntu repository share the same folders for all binaries, irrelevant of which target they're for: intrepid, hardy, i386, amd64 etc...

I assume that the various Packages files in this repository are created with apt-ftparchive.

What I'd like to understand, is how do you configure it so some packages only appear for intrepid, and some others only appear for hardy ?

When I run apt-archive in the folders containing all the .deb files ; it populates hardy and intrepid with exactly the same packages ...

Here is my apt-ftparchive.conf file:
```
Dir {
	ArchiveDir ".";
	CacheDir "/home/avenardj/pcliving/.cache";
};

Default {
	Packages::Compress ". gzip bzip2";
	Sources::Compress ". gzip bzip2";
	Contents::Compress ". gzip bzip2";
};

TreeDefault {
	   BinCacheDB "packages-$(SECTION)-$(ARCH).db";
	   Directory "pool/$(SECTION)";
	   SrcDirectory "pool/$(SECTION)";
	   Packages "$(DIST)/$(SECTION)/binary-$(ARCH)/Packages";
	   SrcPackages "$(DIST)/$(SECTION)/source/Sources";
	   Contents "$(DIST)/Contents-$(ARCH)";
};

Tree "dists/intrepid" {
	Sections "release testing bleeding";
	Architectures "i386 amd64 source";
}

Tree "dists/hardy" {
	Sections "release";
	Architectures "i386 amd64 source";
}

```

And the directory is organised like:
./dists
./dists/hardy
./dists/hardy/release
./dists/hardy/release/binary-amd64
./dists/hardy/release/binary-i386
./dists/hardy/release/source
./dists/intrepid
./dists/intrepid/bleeding
./dists/intrepid/bleeding/binary-amd64
./dists/intrepid/bleeding/binary-i386
./dists/intrepid/bleeding/source
./dists/intrepid/release
./dists/intrepid/release/binary-amd64
./dists/intrepid/release/binary-i386
./dists/intrepid/release/source
./dists/intrepid/testing
./dists/intrepid/testing/binary-amd64
./dists/intrepid/testing/binary-i386
./dists/intrepid/testing/source
./pool

I've searched and googled for hours, I can't find my answer.
I was hoping someone would be kind enough to shed some light on this.

Thanks !
Jean-Yves

---

### Post by superm1 on 2009-03-17
Hi Jean:

We actually use the Ubuntu PPA system and mirror our PPA using the mythbuntu-weeklybuild bzr branch.

---

### Post by jyavenard on 2009-03-17
> **superm1 said:**
> Hi Jean:

We actually use the Ubuntu PPA system and mirror our PPA using the mythbuntu-weeklybuild bzr branch.

Thank you for this.

I found also that reprepro could do what I want ...

---

