# Cunliffe, A Lexicon of the Homeric Dialect (1924)

Richard John Cunliffe, *A Lexicon of the Homeric Dialect* (London: Blackie
and Son, 1924), the main lexicon, pages 1 to 430, as structured data: every
entry as a JSON object with its text, senses, references to the Iliad and
Odyssey, cross-references and the page it is printed on. This is release
`cunliffe-2026-11-25`, with 9,852 entries: 9,810 words and
the 42 prefixes and suffixes printed after them.

Not included: the grammatical appendix on pages 431 to 452, and Cunliffe's
separately published index of proper and place names.

## The printed book and the scans

The text is checked against the University of Michigan copy of the 1924
book, digitized by Google and kept by the Internet Archive as
[`mdp.39015005687283`](https://archive.org/details/mdp.39015005687283)
(600 ppi, Public Domain Mark). The leaf of a printed page is the page
number plus 16. `pages.json` gives every page's leaf, a link to it in the
Internet Archive's viewer and a link to its image, checked against the
item's own leaf list and page labels (in `scans/`, as the Internet Archive
serves them).

## How the text was made

The text comes from the Perseus Digital Library's TEI encoding of the
lexicon (`cunliffe.lexentries.unicode.xml` in
[gregorycrane/Homerica](https://github.com/gregorycrane/Homerica), commit
`e1b05d67`), edited by Gregory Crane with many corrections by
Helma Dik. Each entry of the encoding is converted to plain text in printed
order, with the structure (senses, references, cross-references, the
headword and the encoder's marking of glosses) given as spans of that text.

### Conversion rules

These rules apply to every entry, so that the text reads as printed where
the encoding writes it another way. They are not corrections and are not
recorded in `corrections.json`:

- References are written as Cunliffe prints them: the book of the Iliad as
  a capital letter, of the Odyssey as a small one, and a further line of the
  same book as a bare number (`Ξ 113, Φ 109: δ 611, 612`). Each one also
  keeps the encoding's form (`encoded`), a CTS URN, and its passage in the
  Open Greek Corpus (`address`), so that a reader can open the line.
- Sense labels are written as printed, `(1)`, `(a)`, `(α)`, before the
  sense. The print's dash before a new sense is not reproduced, and the one
  label the encoder added, τόφρα (4), is left out of the text.
- The head is set as printed: the signs before the headword, the headword,
  its homograph number as a superscript (`ἄγη¹`) and the punctuation after
  it. Where the encoding has no punctuation there, the print's comma or stop
  is set (`ἀγαθός, -ή, -όν`; `ἀμαυρός. Dim, faint`). The signs are also kept
  in `flags`. Cunliffe's preface: † before a verb means that only the parts
  cited occur, and * before a form means that it is not recorded but
  assumed.
- Where the encoding spells out what the print abbreviates, the printed
  form is set and the encoding's is kept in `source.print_readings`: "prec."
  and "next", which the encoding writes as the headword they stand for
  (`ἀγακλειτός ... = prec.`), and one modernized word.
- References to the senses of an entry are written as printed, each level
  in brackets (`βοή (2)`, `εἴδω (III) (12)`), and a word that the encoding
  repeats for a further sense is named once (`ἐπι- (1) (7)` for the
  encoding's `ἐπι- 1, ἐπι- 7`). The reference's `encoded` keeps the
  encoding's form.
- The homograph numbers of cross-references, and of words cited in an
  etymology, are superscripts as printed (`καρπός¹`, `ἀ-¹`).
- The stop at the end of an etymology bracket stands where the print sets
  it: after a bracket that ends a paragraph (`[τέλος].` where the encoding
  has `[τέλος.]`), and inside a bracket that stands as a sentence of its own
  (`δ 124. [Cf. εἶρος.]`). A list of compounds that stands as a sentence
  takes its stop inside the parenthesis (`(ἐπι-, κατα-.)`).
- There is no space after an opening bracket (`[= γαῖα]` where the encoding
  has `[ = γαῖα]`), and runs of whitespace are single spaces.
- Besides the printed headword, `keys.json` gives each entry the encoder's
  standard spelling of the lemma (ναῦς for νηῦς), the encoding's spelling of
  a headword that a correction changed only in its breathings, accents,
  diaeresis or iota subscript (σῴζω for the printed σώζω), and both forms of
  a headword with a letter in brackets (`ἄνευθε(ν)`: ἄνευθε and ἄνευθεν).

### Corrections

The encoding was then compared with the print, and every difference found
was read on the scan. The corrections are 2,214 reversible
records in `corrections.json`: references with a wrong book letter or line
number, references and text the encoding lost or added, misread or
unmarked headwords (most of them long and short marks the encoding leaves
out), quotation marks, capitals, running heads encoded as text, and entries
the encoding lacks, typed from the scan. Of these, 16
correct Cunliffe himself, where the print is wrong; the rest correct the
encoding. Each one that changes an entry's text or references is marked at that place in the entry, with the reading before it and the reason. The 8 that change no entry's text (2 page breaks and 6 whole entries removed: c0007-c0008, c1960-c1963, c2074, c2082) have no mark. The conversion rules above are applied to every entry
by the converter and are not recorded one by one.

To find the differences, every quotation was compared with the line it
cites, and every reference was checked for the entry's word on or next to
the cited line. References that failed, headwords and a sample of the rest
were read on the scan.

## Quality

Every entry has `quality` `transcribed-checked`: a transcription checked
against the print. 92,926 of the 92,948
references are linked to a passage of the Open Greek Corpus release
`corpus-2026-11-26`, and `reverse/` lists, for every line of the two
poems, the entries that cite it.

## Known problems

- 22 references have no passage: most cite lines that the corpus
  edition (Perseus, Monro's text) omits (Iliad 9.458-461 and 14.269,
  Odyssey 16.101 and 23.49), and two are garbled in the encoding.
- Not every reference has been read on the scan. A reference whose line
  passes the checks can still be wrong, and over a hundred quotations the
  check does not find on their line (mostly words Cunliffe supplies rather
  than quotes) have not all been read.
- Long and short marks inside the entries (in forms and quotations) are as
  the encoding has them. Only the headwords and the notes beside them were
  read on the scan.
- Slips of the corrected kinds that the searches cannot find may remain: a
  name written small that Homer also has as a common word, a space lost
  before a word, a misread letter that still makes a word.
- Columns are not recorded, only pages.

Please report a misreading as an issue on this repository, with the
entry's id and the page.

## Files

The format is open-greek-lexica 0.3.0, described in
[`format.md`](format.md), with JSON Schemas in `schema/`.

| file | content |
|---|---|
| `manifest.json` | title, edition, licence, attribution, the pinned source, the scan, counts, and every file with its size and SHA-256 |
| `entries/0001.jsonl` to `entries/0020.jsonl` | the entries in printed order, one JSON object per line, 500 per file |
| `keys.json` | lookup key -> entry ids, for headword search |
| `pages.json` | one row per printed page: its leaf, links and the entries on it |
| `reverse/<work>.json` | line of the Iliad or Odyssey -> ids of the entries that cite it |
| `corrections.json` | every correction, in the order applied, with its inverse |
| `aliases.json` | retired entry ids -> the ids that replace them |
| `scans/` | the scan's leaf list and page labels, as the Internet Archive serves them |
| `vectors/` | test vectors for the lookup key, the letters-only fold, the Latin transliteration and the corpus reader's words |

An entry's id is the lexicon's id and a local id taken from the Perseus
encoding's own identifier of the entry (`cunliffe-1924:agathos` for ἀγαθός).
An id is never reused; one that has to go is kept in `aliases.json` with
the ids that replace it.

`corrections.json` keeps, for each record, the reading before and after,
whether the print or the encoding was wrong, a one-line reason, the entry
and element it changes, the scan page and the inverse change. The working
evidence behind each record is not part of this repository.

## How to cite

Cite the release you used, by its tag:

> Richard John Cunliffe, A Lexicon of the Homeric Dialect (1924), Open
> Greek digital edition, release `cunliffe-2026-11-25` (2026-11-25),
> https://github.com/open-greek/lexicon-cunliffe. Digital text from the Perseus Digital Library TEI
> encoding (Tufts University), edited by Gregory Crane, with many
> corrections by Helma Dik.

`CITATION.cff` has the same in machine-readable form. Cite an entry by its
id and the release.

## Licence and attribution

The 1924 book is in the public domain. The Perseus TEI encoding carries no
licence statement of its own, and neither does the repository that holds
it; the Perseus Digital Library's own repositories of texts and lexica
(PerseusDL) are released under CC BY-SA 4.0. This dataset, with its
corrections and structure, is released under CC BY-SA 4.0: see `LICENSE`.
Credit it as follows:

> Richard John Cunliffe, A Lexicon of the Homeric Dialect (London: Blackie and Son, 1924). Digital text from the Perseus Digital Library TEI encoding (Tufts University), edited by Gregory Crane, with many corrections by Helma Dik. Converted and corrected by the Open Greek project, CC BY-SA 4.0.

The source text is the Perseus Digital Library's encoding of the lexicon,
Gregory Crane, Editor-in-Chief, Perseus Digital Library, Tufts University
(http://www.perseus.tufts.edu/), with many corrections by Helma Dik:
`cunliffe.lexentries.unicode.xml` in
https://github.com/gregorycrane/Homerica at commit `e1b05d67`.
The corrections to the encoding are all in `corrections.json`, so that they
can be offered back to it. The page images are the University of Michigan
copy, digitized by Google (Internet Archive, Public Domain Mark 1.0).
