# DNA file format

**DNA** is a **file format** that describes DNA. It can be used to store information about the DNA of any natural organisms, it can be any animal, plant, fungi or microorganism that exist in the planet Earth. Also, it allows to use extraterrestrial nitrogenous bases in order to describe extraterretrial organisms if any scientist in the world finds one in the universe. Additional to that, it can describe any fantasy organism by accepting any custom nitrogenous base needed for that purpose. Thinking like that, any DNA of a fantasy animal or fantasy plant can be described with this file format.

The DNA file format is based on XML and uses the **extension .dna**. It's part of the Scifir Collection, a collection of technologies, between libraries and file formats, that allows scientists to create scientific software and scientific machines. You can see more technologies of the Scifir Collection in the GitHub page of [Scifir](https://github.com/scifir/).

A **dna file** is an **archive file** containing the following files:
- **sequence.dnal** or **sequence.dnac** file: It contains all the DNA sequence. The dnal files is a lighter file format than the dnac file format.
- **info.xml** file: It contains the metadata associated with the genetic information, as is the species of the life form, his name, the authors, the organization (if there's one), among other data.
- **sequence.sha256** file: It's a checksum that forbids to falsify the sequence.dnal or the sequence.dnac file.
- **info.sha256**: It's a checksum that forbids to falsify the info.xml file.

### Advantages
- **Very light:** Compared to other DNA file formats it's by far lighter. Each dna file using a dnal file sizes MB rather than GB. The dna files using dnac file size GB as usual.
- **Very structured:** It allows to change one gene or another by knowing each change made, rather than editing a large DNA sequence. Additional to changing genes, it's easy to add chromosomes.
- **Artificial nitrogenous bases:** Artificial nitrogenous bases can be added, in order to support **artificial DNAs**. An artificial DNA is a concept defined in Scifir to refer to DNA created artificially with extended characteristics related to natural DNA, it's not considered an artificial DNA a natural DNA modified artificially by any means (inside a computer or in the laboratory with injections), only a DNA is an artificial DNA if it has new nitrogenous bases not present on the natural world.
- **Extraterrestrial nitrogenous bases:** Extraterrestrial nitrogenous bases can be added to support any extraterrestrial life form present in the universe, which possibly will be found in a not so distant future.
- **Metadata:** The name of the life form, the name of the species, the authors, the organization, among other metadata, can all be added here.

### Example files
An example of a **dnal file**, the most commonly used between the dnal and the dnac file, is the following:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<dna>
	<chromosome name="1">
		<gene name="human:(hgnc) black_hair"></gene>
		<non_coding name="human:(hgnc) non_coding1"></non_coding>
		<gene name="human:(hgnc) brown_eyes"></gene>
		<gene>ATCGAT</gene>
	</chromosome>
</dna>
```

An example of a **dnac file** is the following:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<dna>
	<chromosome name="1">
		<gene>TGCAATCGAG</gene>
		<non_coding>TAACTAAG</non_coding>
		<gene>ATCGAT</gene>
	</chromosome>
</dna>
```

An example of an **info.xml file** inside a .dna file is the following:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<info>
	<name>Dogo</name>
	<species>dog</species>
	<authors>Ismael Correa Castro</authors>
	<date>2023-07-20</date>
	<description>Very energetic dog.</description>
	<organization independent="true"></organization>
</info>
```

The checksum file **sequence.sha256** and the checksum file **info.sha256** corresponds to a file generated by sha256sum.

### Author

The DNA file format has been created by [Ismael Correa Castro](https://github.com/Iarfen/), an industrial civil engineer and scientist of 32 years old. You can email him if you find bugs, you want to request new features, or have any other need, at ismael.correa.castro@gmail.com. His ORCID is 0009-0007-3815-7053, if you want to reference this work inside any publication.

### Funding

The **Scifir Foundation** is looking for **funding**, in order to do some digital marketing and pay some other needs of his projects. If you want to support his technologies, and **science will thank you** for that, you can donate in this [sponsors page](https://github.com/sponsors/Iarfen).

## XML elements

**dnal** and **dnac** files have the following elements:

| XML element | Use | Description
| -------- | ---------| ----------------------------|
| \<dna\> | Required, top level | Top-level element to represent dna |
| \<chromosome\> | Required, any number | Adds a chromosome |
| \<mtdna\> | Optional | Adds a mitochondrial DNA |
| \<cpdna\> | Optional | Adds a chloroplasts DNA |
| \<gene\> | Required, any number | Adds a gene sequence |
| \<non_coding\> | Required, any number | Adds a non-coding sequence |

**info.xml** files have the following elements:

| XML element | Use | Description
| -------- | ---------|  ----------------------------|
| \<info\> | Required, top level| Top level element to represent metadata of a DNA |
| \<name\> | Optional | Name of the life form |
| \<species\> | Optional | Name of the species the life form is |
| \<authors\> | Required | Name of each of the authors of the DNA sequencing and/or edition |
| \<date\> | Required | Date of creation of the file |
| \<description\> | Optional | Any relevant description of the life form |
| \<organization\> | Required | Organization the authors were working for |

### \<dna\>

The **<dna> element** is the top-level element of **dnal** and **dnac files**. It contains all the other elements.

### \<chromosome\>

The **<chromosome> element** represents a **chromosome**. It contains <gene> and <non_coding> elements in any number.

It has the following attribute:

| Attribute | Required | Description
| -------- | --------- | ----------------------------|
| name | Name of the chromosome to identify it from others |

### \<mtdna\>

The **<mtdna> element** represents a **mitochondrial DNA**. As <chromosome>, it contains <gene> and <non_coding> elements in any number. There can only be one in a DNA file, and can be optionally present, because for dna files of plants there doesn't exist the mitochondrial DNA.

### \<cpdna\>

The **<cpdna> element** represents a **chloroplast DNA**. It's similar to the <mtdna> element, and contains <gene> and <non_coding> elements in any number. It can be optionally present, because for dna files of animals there doesn't exist chloroplasts.

### \<gene\>

The **<gene> element** represents a **gene**. It contains the sequence of nitrogenous bases of which the gene is composed of. The nitrogenous bases are specified in lower case letters if they are not methylated, and they are specified in upper case letters if they are methylated. It's very important to use lower case letters or upper case letters appropiately, because the methylation of nitrogenous bases can seriously change the behavior of part of the DNA.

Given the fact that, coming from the theory of codons, genes should always start with AUG, any <gene> element that doesn't starts with that sequence should be wrong. In order to support any possible biological case, to start with AUG is not expressly supported.

### \<non_coding\>

The **<non_coding> element** represents a **non-coding region of the DNA**. It usually comprises the majority of nitrogenous bases in any DNA file, because the DNA of life forms usually contains a majority of non-coding regions. It's usually edited in small portions, specifically, in the portions of the transcription factors, to change the level of expression of some specific gene, which usually is the gene that comes next (if the region of the transcription factor is near the end of the non-coding region), or the gene that was previously (if the region of the transcription factor is near the start of the non-coding region).
