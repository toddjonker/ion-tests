# Amazon Ion Test Data

This package contains a variety of test data for implementations of the
[Amazon Ion](https://amazon-ion.github.io/ion-docs) data format.

The `catalog` folder contains Ion catalog data: shared symbol tables and modules
that are available for use by all other parts of this test suite.

The `conformance` folder contains formal test cases for Ion implementations,
expressed using a small, declarative domain-specific language.

The `iontestdata*` folders contain samples of Ion
content for use by compatibility test suites.

Consumers must assume that additional nested subfolders may be added, and
should therefore recurse down from the desired folder if appropriate.

## Ion 1.0

Ion 1.0 test data is found in `iontestdata`.

The content is partitioned as follows:

  * `bad`

      All files in this directory are invalid Ion and should fail parsing.
      Most files should include comments indicating the problem.

  * `good`

      All files in this directory are valid Ion.

  * `good/equivs`

      Each file in this directory consists of one or more top-level sequences
      (lists or sexps). Each top-level sequence contains at least two Ion
      values, all of which should be equivalent within the Ion data model.
      This equivalence constraint does not apply to child values of different
      top-level sequences.

  * `good/non-equivs`

      Each file in this directory consists of one or more top-level sequences
      (lists or sexps). Each top-level sequence contains at least two Ion
      values, all of which should NOT be equivalent within the Ion data model.
      This equivalence constraint does not apply to child values of different
      top-level sequences.

Additional constraints:

  * `good/timestamps`

      Each .ion file must have one or more top-level timestamp values,
      one per line.
      Comments must be //-style and start at the first column.
      Subdirectories do not necessarily follow this convention.

  * `bad/timestamps`

      Each .ion file must have a single invalid timestamp as the first line.
      Comments may follow on subsequent lines.
      Subdirectories do not necessarily follow this convention.
  * `good/equivs` and `good/non-equivs`

      If a top-level sequence is annotated with "embedded_documents", it denotes
      that each of its Ion values is to be parsed as a Ion string value, where
      its string value is to be parsed as a document.
      As such, each top-level sequence contains at least two documents, all of
      which should be equivalent or non-equivalent within the Ion data model,
      for the directories good/equivs and good/non-equivs respectively.


## Ion 1.1

Ion 1.1 test data is found in `iontestdata_1_1`.

The content is partitioned as follows:

* `bad`

  All files in this directory are invalid Ion and should fail parsing.
  Most files should include comments indicating the problem.

* `good`

  All files in this directory are valid Ion.

* `good/equivs`

  Each file in this directory consists of one or more top-level containers.
  (structs, lists, or sexps). Each top-level sequence contains at least two 
  Ion values, all of which should be equivalent within the Ion data model.
  This equivalence constraint does not apply to child values of different
  top-level sequences.
  When the container is a struct, the field name is used to provide a
  description of the value being tested. 

* `good/non-equivs`

  Each file in this directory consists of one or more top-level containers.
  (structs, lists, or sexps). Each top-level sequence contains at least two
  Ion values, all of which should NOT be equivalent within the Ion data model.
  This equivalence constraint does not apply to child values of different
  top-level sequences.
  When the container is a struct, the field name is used to provide a
  description of the value being tested.

Additional constraints:

* `good/timestamps`

  Each .ion file must have one or more top-level timestamp values,
  one per line.
  Comments must be //-style and start at the first column.
  Subdirectories do not necessarily follow this convention.

* `bad/timestamps`

  Each .ion file must have a single invalid timestamp as the first line.
  Comments may follow on subsequent lines.
  Subdirectories do not necessarily follow this convention.

* `good/equivs` and `good/non-equivs`

  If a top-level container is annotated with "embedded_documents", each
  value it contains must be an Ion String or Ion Blob. Each value is to be 
  parsed as a Text Ion or Binary Ion document respectively.
  As such, each top-level container contains at least two documents, all of
  which should be equivalent or non-equivalent within the Ion data model,
  for the directories good/equivs and good/non-equivs respectively.
