---
swagger: "2.0"
x-collection-name: Wordnik
x-complete: 0
info:
  title: Wordnik Adds words to a WordList
  description: Adds words to a wordlist.
  version: "4.0"
host: api.wordnik.com
basePath: /v4
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /account.json/wordLists:
    get:
      summary: Fetches WordList objects for the logged-in user.
      description: Fetches wordlist objects for the logged-in user..
      operationId: getWordListsForLoggedInUser
      x-api-path-slug: account-jsonwordlists-get
      parameters:
      - in: header
        name: auth_token
        description: auth_token of logged-in user
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: skip
        description: Results to skip
      responses:
        200:
          description: OK
      tags:
      - Account
      - Words
      - Lists
  /word.json/{word}:
    get:
      summary: Given a word as a string, returns the WordObject that represents it
      description: Given a word as a string, returns the wordobject that represents
        it.
      operationId: getWord
      x-api-path-slug: word-jsonword-get
      parameters:
      - in: query
        name: includeSuggestions
        description: Return suggestions (for correct spelling, case variants, etc
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: String value of WordObject to return
      responses:
        200:
          description: OK
      tags:
      - Words
  /word.json/{word}/audio:
    get:
      summary: Fetches audio metadata for a word.
      description: The metadata includes a time-expiring fileUrl which allows reading
        the audio file directly from the API.  Currently only audio pronunciations
        from the American Heritage Dictionary in mp3 format are supported.
      operationId: getAudio
      x-api-path-slug: word-jsonwordaudio-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: useCanonical
        description: Use the canonical form of the word
      - in: path
        name: word
        description: Word to get audio for
      responses:
        200:
          description: OK
      tags:
      - Words
      - Audio
  /word.json/{word}/definitions:
    get:
      summary: Return definitions for a word
      description: Return definitions for a word.
      operationId: getDefinitions
      x-api-path-slug: word-jsonworddefinitions-get
      parameters:
      - in: query
        name: includeRelated
        description: Return related words with definitions
      - in: query
        name: includeTags
        description: Return a closed set of XML tags in response
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: partOfSpeech
        description: CSV list of part-of-speech types
      - in: query
        name: sourceDictionaries
        description: Source dictionary to return definitions from
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to return definitions for
      responses:
        200:
          description: OK
      tags:
      - Words
      - Definitions
  /word.json/{word}/etymologies:
    get:
      summary: Fetches etymology data
      description: Fetches etymology data.
      operationId: getEtymologies
      x-api-path-slug: word-jsonwordetymologies-get
      parameters:
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to return
      responses:
        200:
          description: OK
      tags:
      - Words
      - Etymologies
  /word.json/{word}/examples:
    get:
      summary: Returns examples for a word
      description: Returns examples for a word.
      operationId: getExamples
      x-api-path-slug: word-jsonwordexamples-get
      parameters:
      - in: query
        name: includeDuplicates
        description: Show duplicate examples from different sources
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: skip
        description: Results to skip
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to return examples for
      responses:
        200:
          description: OK
      tags:
      - Words
      - Examples
  /word.json/{word}/frequency:
    get:
      summary: Returns word usage over time
      description: Returns word usage over time.
      operationId: getWordFrequency
      x-api-path-slug: word-jsonwordfrequency-get
      parameters:
      - in: query
        name: endYear
        description: Ending Year
      - in: query
        name: startYear
        description: Starting Year
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to return
      responses:
        200:
          description: OK
      tags:
      - Words
      - Frequency
  /word.json/{word}/hyphenation:
    get:
      summary: Returns syllable information for a word
      description: Returns syllable information for a word.
      operationId: getHyphenation
      x-api-path-slug: word-jsonwordhyphenation-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: sourceDictionary
        description: Get from a single dictionary
      - in: query
        name: useCanonical
        description: If true will try to return a correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to get syllables for
      responses:
        200:
          description: OK
      tags:
      - Words
      - Hyphenation
  /word.json/{word}/phrases:
    get:
      summary: Fetches bi-gram phrases for a word
      description: Fetches bi-gram phrases for a word.
      operationId: getPhrases
      x-api-path-slug: word-jsonwordphrases-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: query
        name: wlmi
        description: Minimum WLMI for the phrase
      - in: path
        name: word
        description: Word to fetch phrases for
      responses:
        200:
          description: OK
      tags:
      - Words
      - Phrases
  /word.json/{word}/pronunciations:
    get:
      summary: Returns text pronunciations for a given word
      description: Returns text pronunciations for a given word.
      operationId: getTextPronunciations
      x-api-path-slug: word-jsonwordpronunciations-get
      parameters:
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: query
        name: sourceDictionary
        description: Get from a single dictionary
      - in: query
        name: typeFormat
        description: Text pronunciation type
      - in: query
        name: useCanonical
        description: If true will try to return a correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to get pronunciations for
      responses:
        200:
          description: OK
      tags:
      - Words
      - Pronunciations
  /word.json/{word}/relatedWords:
    get:
      summary: Given a word as a string, returns relationships from the Word Graph
      description: Given a word as a string, returns relationships from the word graph.
      operationId: getRelatedWords
      x-api-path-slug: word-jsonwordrelatedwords-get
      parameters:
      - in: query
        name: limitPerRelationshipType
        description: Restrict to the supplied relationship types
      - in: query
        name: relationshipTypes
        description: Limits the total results per type of relationship type
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to fetch relationships for
      responses:
        200:
          description: OK
      tags:
      - Words
      - RelatedWords
  /word.json/{word}/topExample:
    get:
      summary: Returns a top example for a word
      description: Returns a top example for a word.
      operationId: getTopExample
      x-api-path-slug: word-jsonwordtopexample-get
      parameters:
      - in: query
        name: useCanonical
        description: If true will try to return the correct word root (cats -> cat)
      - in: path
        name: word
        description: Word to fetch examples for
      responses:
        200:
          description: OK
      tags:
      - Words
      - TopExample
  /wordList.json/{permalink}/words:
    get:
      summary: Fetches words in a WordList
      description: Fetches words in a wordlist.
      operationId: getWordListWords
      x-api-path-slug: wordlist-jsonpermalinkwords-get
      parameters:
      - in: header
        name: auth_token
        description: The auth token of the logged-in user, obtained by calling /account
      - in: query
        name: limit
        description: Maximum number of results to return
      - in: path
        name: permalink
        description: ID of WordList to use
      - in: query
        name: skip
        description: Results to skip
      - in: query
        name: sortBy
        description: Field to sort by
      - in: query
        name: sortOrder
        description: Direction to sort
      responses:
        200:
          description: OK
      tags:
      - WordList
      - Permalink
      - Words
    post:
      summary: Adds words to a WordList
      description: Adds words to a wordlist.
      operationId: addWordsToWordList
      x-api-path-slug: wordlist-jsonpermalinkwords-post
      parameters:
      - in: header
        name: auth_token
        description: The auth token of the logged-in user, obtained by calling /account
      - in: body
        name: body
        description: Array of words to add to WordList
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: permalink
        description: permalink of WordList to user
      responses:
        200:
          description: OK
      tags:
      - WordList
      - Permalink
      - Words
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---