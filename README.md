## Overview
- `github_release_dataset.jsonl` は 1 行 1 アノテーションの JSONL です。
- 総アノテーション数は `124`、ユニークアイデア数は `42`、匿名化済みアノテータ数は `8` です。
- 各行には、人手アノテーション、比較用の派生指標、対応するアイデア本文が入っています。

## Row structure
- `unique_key`: アイデアを一意に識別するキーです。
- `source_file`, `idea_id`, `idea_name`: アイデア識別子と表示名です。
- `annotator`: 匿名化済みアノテータ ID です。
- `company_or_domain`, `technology_or_asset`, `segment_meta`: アイデアの企業・技術・対象セグメント情報です。
- `annotation`: 人手アノテーション本体です。
- `derived_metrics`: 人手値と LLM 値を比較しやすくした派生指標です。
- `idea`: 当該アノテーションに対応するアイデア本文です。

## Annotation fields
- `annotation.tam`, `annotation.sam`, `annotation.som_y3` は人手推定値です。`base` は円単位です。
- `annotation.decomposition` は因数分解の各因子です。
- `annotation.notes` はアノテータの補足説明です。
- `annotation.llm_annotation` は LLM 側の推定値です。
- `annotation.llm_eval` は人手による LLM 推定の評価です。

## Derived fields
- `tam_base_oku`, `sam_base_oku`, `som_base_oku` は人手推定値を億円単位に変換した列です。
- `gpt_*`, `gem_*` は GPT / Gemini の推定値、評価ラベル、コメント、比較指標です。
- `*_ratio_*` は人手値と LLM 値の比率、または市場サイズ間の比率です。
- `timestamp_dt` は `timestamp` を日時型相当に整形した値です。

## Idea fields
- `idea.name`, `idea.description` はアイデア名と本文です。
- `idea.segment`, `idea.job_to_be_done` は対象顧客と課題設定です。
- `idea.business_model`, `idea.key_risks`, `idea.assumptions` は事業モデル補足です。

## Annotator labels
- `professional-1`, `professional-2` は専門家です。
- `non-professional-N`は非専門家です。

## Full field list for `derived_metrics`
- `timestamp_dt`, `tam_base_oku`, `sam_base_oku`, `som_base_oku`, `som_to_tam_ratio`, `sam_to_tam_ratio`, `gpt_tam_base_oku`, `gpt_sam_base_oku`, `gpt_som_base_oku`, `gpt_som_ratio_human_to_llm`, `gpt_tam_judgement`, `gpt_sam_judgement`, `gpt_som_judgement`, `gpt_som_formula_judgement`, `gpt_comment`, `gpt_som_formula_comment`, `gpt_som_judge_score`, `gem_tam_base_oku`, `gem_sam_base_oku`, `gem_som_base_oku`, `gem_som_ratio_human_to_llm`, `gem_tam_judgement`, `gem_sam_judgement`, `gem_som_judgement`, `gem_som_formula_judgement`, `gem_comment`, `gem_som_formula_comment`, `gem_som_judge_score`
